# 위키 작성 가이드

## 1. 위키의 목적

위키는 **시간이 지나도 가치를 유지하는 정적 지식**을 정리하는 공간입니다. 시계열 기록(R&D 로그)과 달리, 위키 문서는 지속적으로 업데이트되어 항상 최신 상태를 유지해야 합니다.

## 2. 카테고리별 작성 영역

| 카테고리 | 경로 | 내용 |
|---------|------|------|
| 시작하기 | `wiki/getting-started/` | 신규 합류자 온보딩, 환경 셋업 |
| 이론 | `wiki/theory/` | 자율주행/ML 핵심 이론, 알고리즘 설명 |
| 기술 스택 | `wiki/tech-stack/` | CARLA, PyTorch, ROS2 등 도구 사용법 |
| 아키텍처 | `wiki/architecture/` | 시스템 설계, 데이터 흐름, 컴포넌트 명세 |

## 3. 표준 문서 구조

모든 위키 문서는 다음과 같은 표준 구조를 따릅니다.

```markdown
# [문서 제목]

## 1. 개요 (Overview)
이 문서가 다루는 주제와 독자가 얻을 수 있는 정보를 1~2문단으로 요약합니다.

## 2. 핵심 개념 (Core Concepts)
주제와 관련된 핵심 용어와 개념을 정의합니다. 표를 적극 활용합니다.

## 3. 숭산텍 프로젝트에서의 적용
이 주제가 숭산텍 프로젝트에서 어떻게 사용되는지 구체적인 예시와 함께 설명합니다.

## 4. 코드 예시 / 다이어그램
가능한 한 동작하는 코드 스니펫이나 Mermaid 다이어그램을 포함합니다.

## 5. 더 알아보기 / 참고 문헌
관련된 외부 자료 또는 사내 다른 위키 문서를 링크합니다.
```

## 4. 마크다운 활용 팁

### 4.1 Admonition (강조 박스)

```markdown
!!! note "참고"
    이 부분은 추가 정보입니다.

!!! warning "주의"
    이 설정은 프로덕션에서 사용하지 마세요.

!!! tip "Pro Tip"
    이 명령어는 디버깅에 매우 유용합니다.
```

### 4.2 코드 블록 + 줄 번호

````markdown
```python title="bc_model.py" linenums="1" hl_lines="3 5"
import torch.nn as nn

class BehavioralCloningModel(nn.Module):
    def __init__(self):
        self.backbone = resnet18(...)
```
````

### 4.3 Mermaid 다이어그램

````markdown
```mermaid
flowchart LR
    A[입력] --> B[처리] --> C[출력]
```
````

### 4.4 수식 (LaTeX)

```markdown
인라인 수식: \(\alpha + \beta\)

블록 수식:
$$
\mathcal{L}(\theta) = \mathbb{E}_{(o, a) \sim D} \left[ \| \pi_\theta(o) - a \|^2 \right]
$$
```

## 5. 작성 톤 & 스타일

- **격식 있는 평어체**: "...합니다", "...입니다" 형태로 작성합니다.
- **불필요한 비유 자제**: 기술 문서는 정확성이 우선입니다.
- **코드/명령어**: 백틱(`` ` ``)으로 감싸 명확히 구분합니다.
- **약어 사용**: 첫 등장 시 풀어쓰고 약어를 병기합니다. (예: 행동 복제(Behavioral Cloning, BC))

## 6. 이미지 추가

이미지는 `docs/assets/img/wiki/` 아래에 카테고리별 폴더로 분류하여 저장합니다.

```markdown
![데이터 파이프라인 아키텍처](../assets/img/wiki/data-pipeline-arch.png)
```
