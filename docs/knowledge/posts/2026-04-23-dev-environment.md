---
title: "개발 환경 셋업"
date: 2026-04-23
categories:
  - 시작하기 (Getting Started)
authors:
  - sit
---

본 문서는 숭산텍 자율주행 프로젝트(`Autonomous-Driving-Planning`)에 처음 합류하는 팀원이 로컬 개발 환경을 구축하는 절차를 안내합니다.

<!-- more -->

## 1. 시스템 요구사항

| 구분 | 권장 사양 |
|------|----------|
| OS | Windows 11 (CARLA Host) + WSL2 Ubuntu 22.04 (Client) |
| GPU | NVIDIA RTX 30/40 시리즈 이상 (VRAM 12GB 이상) |
| RAM | 32GB 이상 |
| 저장공간 | 500GB SSD 이상 (수집 데이터 저장용) |
| Python | 3.10 이상 |

## 2. CARLA 시뮬레이터 설치

```bash
# Windows Host
# 1. CARLA 0.9.15 공식 릴리스 다운로드
# https://github.com/carla-simulator/carla/releases/tag/0.9.15

# 2. 압축 해제 후 CarlaUE4.exe 실행
# 3. -quality-level=Low 옵션으로 가벼운 모드 실행 가능
```

## 3. Python 환경 (WSL2)

```bash
# 가상환경 생성
python3.10 -m venv .venv
source .venv/bin/activate

# 의존성 설치
pip install -r requirements.txt

# CARLA Python API 설치
pip install carla==0.9.15
```

## 4. ROS2 Humble 설치 (Phase 2-C 진입 시)

```bash
# Ubuntu 22.04 기준
sudo apt update && sudo apt install -y curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key \
  -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] \
  http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" \
  | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update && sudo apt install -y ros-humble-desktop
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

## 5. 프로젝트 클론 및 검증

```bash
gh repo clone SoongSanTech/Autonomous-Driving-Planning
cd Autonomous-Driving-Planning

# 단위 테스트 실행
pytest tests/ -v

# 데이터 파이프라인 동작 확인
python -m src.data_pipeline.cli --help
```

## 6. 문제 해결

설정 중 문제가 발생하면 [트러블슈팅 R&D 로그](../../rnd/index.md)를 검색하거나, GitHub 이슈를 등록해 주세요.
