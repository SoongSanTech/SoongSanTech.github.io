# CARLA 시뮬레이터

## 1. 개요

**CARLA(Car Learning to Act)**는 Unreal Engine 기반의 오픈소스 자율주행 시뮬레이터로, 자율주행 연구의 사실상 표준(de facto standard)입니다. 숭산텍 프로젝트는 **CARLA 0.9.15** 버전을 사용합니다.

## 2. 핵심 특징

- 사진처럼 사실적인 도시 환경 (Town01~Town10)
- 풍부한 센서 모델 (RGB, Depth, LiDAR, Radar, Semantic Segmentation 등)
- 동적 날씨·시간대 변경
- Python API를 통한 완전한 제어
- ROS Bridge 지원

## 3. 숭산텍 프로젝트의 CARLA 활용

### 3.1 사용 맵

| 맵 | 용도 |
|----|------|
| Town03 | 학습 데이터 수집 (다양한 교차로) |
| Town05 | 평가 (미학습 환경, Generalization 측정) |

### 3.2 센서 구성

| 센서 | 해상도 | FOV | 주기 | 용도 |
|------|--------|-----|------|------|
| Front RGB | 800×600 | 90° | 10Hz | BC/RL 입력 |
| AVM Front/Rear/L/R | 400×300 | 120° | 10Hz | Phase 3+ BEV 연구 |
| GNSS | - | - | 10Hz | 위치 메타데이터 |
| IMU | - | - | 10Hz | 자세 메타데이터 |

### 3.3 동기 모드 (Synchronous Mode)

데이터 수집 시 시뮬레이터와 클라이언트의 동기화를 위해 **Synchronous Mode**를 활용합니다.

```python
import carla

client = carla.Client('localhost', 2000)
world = client.get_world()

settings = world.get_settings()
settings.synchronous_mode = True
settings.fixed_delta_seconds = 0.1  # 10Hz
world.apply_settings(settings)

# 매 틱마다
world.tick()
```

## 4. 자주 발생하는 문제

| 문제 | 해결책 |
|------|--------|
| GPU VRAM 부족 | `-quality-level=Low` 옵션 사용 |
| 클라이언트 타임아웃 | `client.set_timeout(30.0)` 설정 |
| WSL2에서 GUI 표시 안됨 | WSLg 또는 X410 사용, `-RenderOffScreen` 옵션 |
| 충돌 시 시뮬레이터 크래시 | Producer-Consumer 패턴으로 데이터 보존 |

## 5. 참고 자료

- [CARLA 공식 문서](https://carla.readthedocs.io/en/0.9.15/)
- [CARLA Python API Reference](https://carla.readthedocs.io/en/0.9.15/python_api/)
