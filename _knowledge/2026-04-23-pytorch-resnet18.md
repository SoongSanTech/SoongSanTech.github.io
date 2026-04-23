---
title: "PyTorch & ResNet18"
date: 2026-04-23
author: SoongSanTech Team
categories:
  - 기술 스택 (Tech Stack)
---

## 1. 개요

숭산텍은 딥러닝 프레임워크로 **PyTorch 2.x**를, 그리고 BC/RL 모델의 백본으로 **ResNet18**(ImageNet pretrained)을 채택합니다.

<!-- more -->

## 2. 왜 ResNet18인가?

"시스템 우선" 원칙에 따라, 새로운 아키텍처를 발명하기보다는 검증된 모델을 사용하여 파이프라인 전체에 집중합니다. ResNet18 채택의 이유는 다음과 같습니다:

| 이유 | 설명 |
|------|------|
| 입증된 성능 | ImageNet 등 다양한 비전 태스크에서 검증 |
| 경량성 | 약 11M 파라미터로 Jetson 환경에 적합 |
| 풍부한 사전학습 | torchvision에서 가중치 즉시 활용 가능 |
| 단순한 구조 | Skip Connection 외에 특별한 트릭 없음 → 디버깅 용이 |

## 3. 모델 정의 예시

```python
import torch
import torch.nn as nn
from torchvision.models import resnet18, ResNet18_Weights

class BehavioralCloningModel(nn.Module):
    def __init__(self):
        super().__init__()
        # ImageNet pretrained backbone
        self.backbone = resnet18(weights=ResNet18_Weights.IMAGENET1K_V1)
        # 마지막 FC를 제거하고 특징 추출기로만 사용
        self.backbone.fc = nn.Identity()
        # FC Head: 512 -> 256 -> 2 (steering, throttle)
        self.fc_head = nn.Sequential(
            nn.Linear(512, 256),
            nn.ReLU(inplace=True),
            nn.Dropout(0.1),
            nn.Linear(256, 2),
        )
    
    def forward(self, x):
        features = self.backbone(x)  # (B, 512)
        out = self.fc_head(features)  # (B, 2)
        return out
```

## 4. 학습 하이퍼파라미터

| 항목 | 값 |
|------|---|
| Optimizer | AdamW |
| Learning Rate | 1e-4 |
| Weight Decay | 1e-4 |
| Batch Size | 64 |
| Scheduler | CosineAnnealingLR |
| Loss | MSE (multi-task) |
| Epochs | 50 (Early Stopping with patience=5) |

## 5. 입력 전처리

```python
from torchvision import transforms

train_transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.RandomHorizontalFlip(p=0.0),  # 자율주행은 좌우 의미가 다름
    transforms.ColorJitter(brightness=0.2, contrast=0.2, saturation=0.2),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406],
                         std=[0.229, 0.224, 0.225]),
])
```

## 6. 모델 저장 및 체크포인트

학습 중에는 검증 손실 기준으로 best 체크포인트를 저장하며, 양자화 변환을 위해 별도로 ONNX export가 필요합니다.

```python
# Best checkpoint
torch.save({
    'epoch': epoch,
    'backbone': model.backbone.state_dict(),
    'fc_head': model.fc_head.state_dict(),
    'optimizer': optimizer.state_dict(),
    'val_loss': val_loss,
}, 'checkpoints/bc_best.pth')

# ONNX export
dummy_input = torch.randn(1, 3, 224, 224).cuda()
torch.onnx.export(
    model, dummy_input, 'bc_model.onnx',
    input_names=['input'], output_names=['output'],
    opset_version=17,
)
```
