# SoongSanTech.github.io

> **숭산텍(SIT) 자율주행 연구 지식 위키 + R&D 로깅 플랫폼**

[![Deploy](https://github.com/SoongSanTech/SoongSanTech.github.io/actions/workflows/deploy.yml/badge.svg)](https://github.com/SoongSanTech/SoongSanTech.github.io/actions/workflows/deploy.yml)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

🌐 **사이트**: [https://soongsantech.github.io](https://soongsantech.github.io)

---

## 개요

이 레포지토리는 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 기반의 정적 사이트로, 다음 두 가지 목적을 동시에 수행합니다.

1. **지식 위키 (`/wiki`)**: 자율주행, 강화학습, CARLA, ROS2 등 프로젝트의 핵심 개념·기술·아키텍처 문서
2. **R&D 로깅 (`/rnd`)**: 실험·트러블슈팅·마일스톤 회고 등 시계열 연구 기록 (블로그 형식)

## 기술 스택

| 구분 | 기술 |
|------|------|
| 정적 사이트 생성기 | [MkDocs 1.6+](https://www.mkdocs.org/) |
| 테마 | [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) |
| 콘텐츠 형식 | Markdown + PyMdown Extensions |
| 다이어그램 | Mermaid |
| 수식 | MathJax |
| 배포 | GitHub Pages (GitHub Actions) |

## 빠른 시작 (로컬 개발)

```bash
# 1. 클론
gh repo clone SoongSanTech/SoongSanTech.github.io
cd SoongSanTech.github.io

# 2. Python 가상환경 + 의존성 설치
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3. 로컬 서버 실행 (http://127.0.0.1:8000)
mkdocs serve
```

## 디렉토리 구조

```
SoongSanTech.github.io/
├── docs/                        # 모든 콘텐츠
│   ├── index.md                 # 홈
│   ├── about.md                 # 소개
│   ├── wiki/                    # 지식 위키
│   │   ├── getting-started/
│   │   ├── theory/
│   │   ├── tech-stack/
│   │   └── architecture/
│   ├── rnd/                     # R&D 로그 (블로그)
│   │   ├── index.md
│   │   ├── .authors.yml
│   │   └── posts/
│   ├── contributing/            # 협업 가이드
│   ├── includes/                # 재사용 마크다운 (약어집 등)
│   └── assets/                  # 이미지·CSS·JS
├── overrides/                   # Material 테마 부분 오버라이드
├── .github/
│   ├── workflows/deploy.yml     # GitHub Actions 자동 배포
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── mkdocs.yml                   # 사이트 설정
├── requirements.txt             # Python 의존성
└── README.md
```

## 기여하기

기여를 환영합니다! 자세한 절차는 [기여 가이드](https://soongsantech.github.io/contributing/)를 참고해 주세요.

| 기여 종류 | 가이드 |
|----------|--------|
| 위키 문서 작성 | [위키 작성 가이드](https://soongsantech.github.io/contributing/wiki-guide/) |
| R&D 로그 작성 | [R&D 로그 가이드](https://soongsantech.github.io/contributing/rnd-guide/) |
| Git/PR 워크플로우 | [Workflow 문서](https://soongsantech.github.io/contributing/workflow/) |

## 라이선스

- **사이트 콘텐츠 (`docs/`)**: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ko)
- **사이트 소스 코드 (`mkdocs.yml`, 워크플로우 등)**: [MIT License](LICENSE)

## 관련 레포지토리

- [SoongSanTech/Autonomous-Driving-Planning](https://github.com/SoongSanTech/Autonomous-Driving-Planning) - 핵심 자율주행 프로젝트
