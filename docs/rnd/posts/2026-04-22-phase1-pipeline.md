---
title: "[Phase 1] CARLA 멀티카메라 데이터 수집 파이프라인 구축 완료"
date: 2026-04-22
categories:
  - R&D
  - Experiments
tags:
  - carla
  - data-pipeline
  - ros2
authors:
  - sit
---

## 1. 개요 및 목표

자율주행 모델(BC/RL) 학습을 위해서는 고품질의 주행 데이터가 필수적입니다. 이번 Phase 1의 목표는 **CARLA 0.9.15 환경에서 전방 RGB 카메라와 AVM 4대 카메라 데이터를 10Hz 주기로 안정적으로 수집하는 파이프라인을 구축**하는 것이었습니다.

<!-- more -->

## 2. 설계 및 구현: Producer-Consumer 패턴

가장 큰 기술적 난제는 시뮬레이터 틱(Tick) 주기와 디스크 I/O 속도 간의 불일치로 인한 프레임 드롭(Frame Drop)이었습니다. 이를 해결하기 위해 **Producer-Consumer 아키텍처**를 도입했습니다.

### 핵심 컴포넌트

- **`SynchronousModeController` (Producer)**
  - 10Hz 고정 주기로 CARLA 서버 틱을 동기화
  - 센서 데이터를 캡처하여 메모리 큐(Queue)에 즉시 푸시
- **`AsyncDataLogger` (Consumer)**
  - 2개의 워커 스레드(Worker Threads)가 큐에서 데이터를 꺼내 디스크에 비동기 기록
  - 큐 크기 1000으로 버퍼링 설정
- **`EpisodeManager`**
  - 5분 주기로 날씨(Clear/Rain/Fog)와 시간대(Day/Night/Backlight)를 자동 전환하여 데이터 다양성 확보

## 3. 테스트 및 검증 결과

단위 테스트와 통합 테스트(pytest + Hypothesis) 총 89개를 작성하여 파이프라인의 안정성을 검증했습니다.

| 검증 항목 | 목표 기준 | 달성 결과 |
|-----------|-----------|-----------|
| 프레임 동기화 | 10Hz 유지 | 평균 10.02Hz 달성 |
| 데이터 손실률 | 1% 미만 | 0.05% 미만 (디스크 I/O 병목 해소) |
| 장애 복원력 | CARLA 크래시 시 데이터 보존 | 테스트 통과 (종료 전 큐 플러시 구현) |

## 4. 향후 계획 (Phase 2-A)

파이프라인 구축이 완료됨에 따라, 수집된 데이터를 바탕으로 **ResNet18 기반 행동복제(Behavioral Cloning, BC) 모델 초기 학습**에 돌입할 예정입니다.

초기에는 전방 단일 카메라(Front RGB) 이미지만을 사용하여 모델을 훈련시키고, 엣지 디바이스(Jetson) 배포를 고려한 224x224 해상도 최적화 작업도 병행할 계획입니다.
