---
title: "강화학습 PPO (Proximal Policy Optimization)"
date: 2026-04-23
author: SoongSanTech Team
cover: /assets/img/rnd/post_bc_rl.png
categories:
  - 이론 (Theory)
---

## 1. 개념

**PPO(Proximal Policy Optimization)**는 OpenAI에서 제안한 정책 경사(Policy Gradient) 계열의 강화학습 알고리즘으로, 학습 안정성과 구현 단순성의 균형이 우수하여 자율주행 연구에서 가장 널리 사용되는 알고리즘 중 하나입니다.

<!-- more -->

## 2. 핵심 아이디어: Clipped Surrogate Objective

PPO는 한 번의 업데이트에서 정책이 너무 크게 변하지 않도록 제약을 두는 방식으로 안정성을 확보합니다.

$$
L^{CLIP}(\theta) = \hat{\mathbb{E}}_t \left[ \min\left( r_t(\theta) \hat{A}_t, \; \text{clip}(r_t(\theta), 1-\epsilon, 1+\epsilon) \hat{A}_t \right) \right]
$$

여기서:
- $r_t(\theta) = \frac{\pi_\theta(a_t|s_t)}{\pi_{\theta_{old}}(a_t|s_t)}$: 정책 비율
- $\hat{A}_t$: 어드밴티지 추정치
- $\epsilon$: 클리핑 파라미터 (보통 0.1~0.2)

## 3. Actor-Critic 구조

PPO는 두 개의 네트워크를 학습합니다.

| 네트워크 | 역할 |
|---------|------|
| Actor (정책 네트워크) | 주어진 상태에서 행동 분포를 출력 |
| Critic (가치 네트워크) | 주어진 상태의 기대 누적 보상을 추정 |

## 4. 숭산텍 프로젝트에서의 PPO

### 4.1 BC Warm-Start 전략

숭산텍은 PPO 학습 시 BC 모델의 가중치를 활용하는 **BC Warm-Start** 전략을 채택합니다. 코드 수준에서 다음과 같이 구현됩니다:

```python
class RLPolicyNetwork(nn.Module):
    @classmethod
    def from_bc_checkpoint(cls, bc_checkpoint_path):
        """BC 체크포인트로부터 RL 정책을 초기화"""
        policy = cls()
        # BC backbone과 FC head를 Actor head로 복사
        bc_state = torch.load(bc_checkpoint_path)
        policy.backbone.load_state_dict(bc_state['backbone'])
        policy.actor_head.load_state_dict(bc_state['fc_head'])
        # Critic head는 새로 초기화
        return policy
```

### 4.2 보상 함수 설계

| 구성 요소 | 가중치 | 설명 |
|----------|--------|------|
| 차선 유지 | +1.0 | 차선 중앙으로부터의 거리에 반비례 |
| 충돌 페널티 | -100.0 | 충돌 발생 시 즉시 큰 음의 보상 |
| 조향 부드러움 | -0.1 | 급격한 조향 변화 방지 |
| 전진 보상 | +0.01 | 단위 시간당 전진 거리 |

### 4.3 학습 환경

- **시뮬레이터**: CARLA 0.9.15
- **Gym 래퍼**: Gymnasium 인터페이스로 표준화
- **에피소드 길이**: 최대 1,000 스텝 (또는 충돌 시 종료)
- **학습 에피소드**: 5,000 회

## 5. 참고 문헌

- [Proximal Policy Optimization Algorithms (Schulman et al., 2017)](https://arxiv.org/abs/1707.06347)
- [Stable Baselines3 PPO 문서](https://stable-baselines3.readthedocs.io/en/master/modules/ppo.html)
