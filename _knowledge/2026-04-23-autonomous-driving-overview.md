---
title: "자율주행 개요"
date: 2026-04-23
author: SoongSanTech Team
categories:
  - 이론 (Theory)
---

## 1. 자율주행이란

자율주행(Autonomous Driving)은 차량이 사람의 직접적 조작 없이 주변 환경을 인식하고, 주행 경로를 계획하며, 차량을 제어하는 기술의 총칭입니다. 일반적으로 SAE(Society of Automotive Engineers) 분류에 따라 **Level 0부터 Level 5**까지의 자율 단계로 구분됩니다.

| 레벨 | 명칭 | 설명 |
|------|------|------|
| L0 | No Automation | 사람이 모든 운전을 담당 |
| L1 | Driver Assistance | 가속/제동 또는 조향 중 하나만 보조 |
| L2 | Partial Automation | 가속/제동·조향 모두 보조하나 사람 감독 필수 |
| L3 | Conditional Automation | 특정 조건에서 시스템이 주행, 비상시 사람 개입 |
| L4 | High Automation | 특정 영역(ODD) 내에서 완전 자율 |
| L5 | Full Automation | 모든 환경에서 완전 자율 |

<!-- more -->

## 2. 자율주행 시스템의 표준 구성

```mermaid
flowchart LR
    A[센서<br>카메라/LiDAR/IMU] --> B[인식<br>Perception]
    B --> C[예측<br>Prediction]
    C --> D[계획<br>Planning]
    D --> E[제어<br>Control]
    E --> F[액추에이터<br>조향/가속/제동]
```

전통적 자율주행 시스템은 위와 같이 모듈식(Modular) 파이프라인으로 구성되며, 각 모듈이 명확한 책임을 가집니다.

## 3. End-to-End 학습 접근법

NVIDIA의 PilotNet(2016)을 시작으로, 카메라 입력에서 직접 조향 명령을 출력하는 **End-to-End 신경망 접근법**이 부상했습니다. 모듈 간 정보 손실이 없고 데이터 기반 최적화가 가능하다는 장점이 있으나, 의사결정 과정의 해석이 어렵고 안전성 검증이 까다롭다는 한계도 존재합니다.

숭산텍 프로젝트는 이 End-to-End 접근법을 채택하되, **CARLA 시뮬레이터에서의 충분한 검증**과 **양자화·시나리오별 안전성 분석**으로 한계를 보완하는 전략을 취합니다.

## 4. 핵심 학습 패러다임

### 4.1 모방 학습 (Imitation Learning)
전문가(또는 autopilot)의 운전 데이터를 모방하여 정책을 학습. 대표적으로 **행동 복제(Behavioral Cloning, BC)**가 있습니다.

### 4.2 강화 학습 (Reinforcement Learning)
환경과의 상호작용을 통해 보상을 최대화하는 정책을 학습. 자율주행 분야에서는 **PPO(Proximal Policy Optimization)** 등이 주로 사용됩니다.

### 4.3 BC + RL 하이브리드
BC로 안정적 초기 정책을 확보한 후, RL로 미세조정하는 2단계 학습 전략. 숭산텍 프로젝트의 핵심 접근법입니다.

## 5. 더 알아보기

- [행동 복제(BC) 상세](behavioral-cloning.md)
- [강화학습 PPO 상세](reinforcement-learning-ppo.md)
- [Sim-to-Real 전이](sim-to-real.md)
