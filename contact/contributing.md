---
layout: page
title: "기여하기"
description: "위키와 R&D 로그 기여 가이드"
---

# 기여하기 (Contributing Guide)

숭산텍(SIT) 위키와 R&D 로그는 팀원 누구나 기여할 수 있는 **공유 지식 공간**입니다. 이 문서는 새로운 글을 작성하거나 기존 글을 수정하는 표준 절차를 안내합니다.

## 1. 한눈에 보는 기여 흐름

```mermaid
flowchart LR
    A[로컬 환경 셋업] --> B[브랜치 생성<br>docs/* 또는 rnd/*]
    B --> C[글 작성/수정]
    C --> D[로컬 미리보기<br>mkdocs serve]
    D --> E[커밋 & 푸시]
    E --> F[Pull Request 생성]
    F --> G[리뷰 & 머지]
    G --> H[자동 배포<br>GitHub Pages]
```

## 2. 가이드 둘러보기

<div class="grid cards" markdown>

-   :material-book-edit:{ .lg .middle } __위키 작성 가이드__

    ---

    이론·기술·아키텍처 문서를 작성할 때 따라야 할 형식과 톤을 안내합니다.

    [위키 가이드 보기](wiki-guide.md)

-   :material-flask-outline:{ .lg .middle } __R&D 로그 가이드__

    ---

    실험·트러블슈팅·마일스톤 회고 등 R&D 로그를 작성하는 방법을 안내합니다.

    [R&D 가이드 보기](rnd-guide.md)

-   :material-file-document-multiple:{ .lg .middle } __작성 템플릿__

    ---

    위키와 R&D 로그에 사용할 수 있는 표준 마크다운 템플릿을 모아두었습니다.

    [템플릿 보기](templates.md)

-   :material-source-branch:{ .lg .middle } __Git/PR 워크플로우__

    ---

    브랜치 명명 규칙, 커밋 메시지 컨벤션, PR 절차를 안내합니다.

    [워크플로우 보기](workflow.md)

</div>

## 3. 기여 시 핵심 원칙

1. **명확성**: 기술 용어는 약어집(`includes/abbreviations.md`)을 활용하여 통일합니다.
2. **재현성**: 실험 로그는 누구나 동일한 결과를 재현할 수 있도록 환경·하이퍼파라미터·시드를 명시합니다.
3. **시각화**: 복잡한 개념은 Mermaid 다이어그램, 표, 수식을 적극적으로 활용합니다.
4. **연결성**: 관련 문서는 상호 링크하여 지식 그래프를 형성합니다.
