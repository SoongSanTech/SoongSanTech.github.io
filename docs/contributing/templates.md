# 작성 템플릿 모음

이 문서는 위키와 R&D 로그를 작성할 때 그대로 복사해 사용할 수 있는 표준 템플릿을 모아두었습니다.

## 1. 위키: 이론 문서 템플릿

```markdown
# [개념명] (영문 표기)

## 1. 정의
한두 문장으로 명확히 정의합니다.

## 2. 수학적 / 알고리즘적 배경
$$
수식
$$

## 3. 숭산텍 프로젝트에서의 적용
- 어디에 사용되는가
- 왜 채택했는가
- 한계와 보완책

## 4. 코드 예시 (필요시)
```python
# ...
```

## 5. 참고 문헌
- `[논문 제목 (저자, 연도)](https://example.com/paper)`
```

## 2. 위키: 기술 스택 가이드 템플릿

```markdown
# [도구명]

## 1. 개요
무엇이며, 왜 이 도구를 사용하는가.

## 2. 핵심 특징
| 특징 | 설명 |
|------|------|
| ... | ... |

## 3. 숭산텍 프로젝트에서의 활용
- 사용 버전
- 주요 사용 영역

## 4. 설치 / 설정 명령
```bash
# 명령어
```

## 5. 자주 발생하는 문제와 해결
| 문제 | 해결책 |
|------|-------|

## 6. 참고 자료
- 공식 문서, 튜토리얼 링크
```

## 3. 위키: 아키텍처 문서 템플릿

```markdown
# [컴포넌트명] 아키텍처

## 1. 개요
이 컴포넌트의 역할과 책임.

## 2. 다이어그램
```mermaid
flowchart TB
    ...
```

## 3. 핵심 모듈 명세
| 모듈 | 책임 |
|------|------|

## 4. 데이터/메시지 형식
```yaml
example:
  field: value
```

## 5. 장애 / 안전 정책

## 6. 사용 예시
```bash
# CLI 또는 코드 예시
```
```

## 4. R&D 로그: 실험 기록 템플릿

```markdown
---
title: "[Phase X-Y] 실험 제목"
date: YYYY-MM-DD
categories:
  - R&D
  - Experiments
tags:
  - tag1
  - tag2
authors:
  - sit
---

## 1. 가설 (Hypothesis)
- H1: ...
- H2: ...

<!-- more -->

## 2. 실험 환경
| 항목 | 값 |
|------|---|
| Git Commit | abcdef0 |
| 데이터 경로 | data/YYYY-MM-DD_*/ |
| 시드 | 42 |
| 하드웨어 | RTX 4090, Driver 555.x |

## 3. 하이퍼파라미터
| 항목 | 값 |
|------|---|
| LR | 1e-4 |
| Batch | 64 |

## 4. 결과
### 4.1 정량 메트릭
| 메트릭 | 값 |
|--------|----|
| MAE Steering | 0.083 |

### 4.2 학습 곡선
![Loss Curve](../assets/img/rnd/YYYY-MM-DD-slug/loss.svg)

## 5. 분석
- 무엇이 잘 됐고
- 무엇이 안 됐는가

## 6. 다음 단계
- [ ] 후속 실험 1
- [ ] 후속 실험 2
```

## 5. R&D 로그: 트러블슈팅 템플릿

```markdown
---
title: "[Troubleshooting] CARLA 클라이언트 타임아웃 해결"
date: YYYY-MM-DD
categories:
  - R&D
  - Troubleshooting
tags:
  - carla
  - bug
authors:
  - sit
---

## 1. 증상
- 명령: `python -m src.data_pipeline.cli collect --duration 1800`
- 에러:
  ```
  RuntimeError: Network operation has timed out
  ```

<!-- more -->

## 2. 재현 조건
- CARLA 0.9.15
- WSL2 Ubuntu 22.04
- GPU 부하 80% 이상일 때 자주 발생

## 3. 원인 분석
... (로그, 디버깅 과정 기술)

## 4. 해결
```python
# Before
client = carla.Client('localhost', 2000)
# After
client = carla.Client('localhost', 2000)
client.set_timeout(30.0)
```

## 5. 교훈
- 모든 외부 통신에는 명시적 타임아웃 설정 권장
- 관련 PR: #42
```

## 6. R&D 로그: 마일스톤 회고 템플릿

```markdown
---
title: "[Milestone] Phase 1 완료 회고"
date: YYYY-MM-DD
categories:
  - R&D
  - Milestones
tags:
  - retrospective
authors:
  - sit
---

## 1. Phase 요약
- 기간: YYYY-MM-DD ~ YYYY-MM-DD
- 목표:
- 달성 결과:

<!-- more -->

## 2. 잘 된 것 (Keep)
1. ...

## 3. 개선이 필요한 것 (Problem)
1. ...

## 4. 다음 Phase에서 시도할 것 (Try)
1. ...

## 5. 메트릭 요약
| 메트릭 | 목표 | 달성 |
|--------|------|------|
```
