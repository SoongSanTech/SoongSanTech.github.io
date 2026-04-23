---
title: "기술 스택 뱃지 가이드"
date: 2026-04-23
author: SoongSanTech Team
categories:
  - 시작하기 (Getting Started)
tags:
  - Guidelines
  - Badges
---

숭산텍 위키와 R&D 로그 작성 시, 특정 기술 스택을 언급할 때 시각적 가독성을 높이기 위해 **kkram95 뱃지 스타일**을 활용합니다. [kkram95.tistory.com/7](https://kkram95.tistory.com/7)에서 제공하는 `img.shields.io` 포맷을 기반으로 숭산텍의 42dot 하이브리드 테마에 맞게 정리했습니다.

<!-- more -->

## 핵심 언어 및 프레임워크

<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/ROS2-22314E?style=for-the-badge&logo=ros&logoColor=white" alt="ROS2">
</div>

```markdown
<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/ROS2-22314E?style=for-the-badge&logo=ros&logoColor=white" alt="ROS2">
</div>
```

## 인프라 및 도구

<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Ubuntu">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/NVIDIA-76B900?style=for-the-badge&logo=nvidia&logoColor=white" alt="NVIDIA">
  <img src="https://img.shields.io/badge/Amazon_S3-569A31?style=for-the-badge&logo=amazon-s3&logoColor=white" alt="Amazon S3">
</div>

```markdown
<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Ubuntu">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/NVIDIA-76B900?style=for-the-badge&logo=nvidia&logoColor=white" alt="NVIDIA">
  <img src="https://img.shields.io/badge/Amazon_S3-569A31?style=for-the-badge&logo=amazon-s3&logoColor=white" alt="Amazon S3">
</div>
```

## 문서화 및 협업

<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  <img src="https://img.shields.io/badge/MkDocs-Material-4B0082?style=for-the-badge" alt="MkDocs">
  <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown">
</div>

```markdown
<div class="tech-badge-row">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  <img src="https://img.shields.io/badge/MkDocs-Material-4B0082?style=for-the-badge" alt="MkDocs">
  <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown">
</div>
```

## 뱃지 활용 원칙

1. **위치:** 기술 문서의 최상단 '개요' 섹션 직하단에 해당 문서가 다루는 핵심 스택을 `<div class="tech-badge-row">`로 감싸서 배치합니다.
2. **스타일:** 일관성을 위해 `style=for-the-badge` 파라미터를 반드시 포함합니다.
3. **색상:** 브랜드 컬러(Deep Indigo `#4B0082`, Sky Blue `#00BFFF`)와 조화되도록, 가급적 로고 본연의 색상(`logoColor=white`)을 유지합니다.
