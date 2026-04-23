# Git / PR 워크플로우

## 1. 로컬 환경 셋업

처음 한 번만 수행하면 됩니다.

```bash
# 레포지토리 클론
gh repo clone SoongSanTech/SoongSanTech.github.io
cd SoongSanTech.github.io

# Python 가상환경 + MkDocs 의존성 설치
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 2. 일상 작업 흐름

### 2.1 최신 main 동기화

```bash
git checkout main
git pull origin main
```

### 2.2 작업 브랜치 생성

브랜치 명명 규칙:

| 종류 | 패턴 | 예시 |
|------|------|------|
| 위키 추가/수정 | `wiki/<주제>` | `wiki/add-bc-theory` |
| R&D 로그 추가 | `rnd/<날짜-슬러그>` | `rnd/2026-05-03-bc-first-train` |
| 사이트 설정/스타일 | `chore/<내용>` | `chore/update-mkdocs-yml` |
| 버그 수정 | `fix/<내용>` | `fix/broken-mermaid-link` |

```bash
git checkout -b wiki/add-bc-theory
```

### 2.3 글 작성 + 로컬 미리보기

```bash
# 로컬 서버 실행 (변경사항 자동 리로드)
mkdocs serve

# 브라우저에서 http://127.0.0.1:8000 접속하여 확인
```

### 2.4 커밋 메시지 컨벤션

[Conventional Commits](https://www.conventionalcommits.org/) 규약을 따릅니다.

| 타입 | 의미 |
|------|------|
| `feat` | 새 문서 또는 기능 추가 |
| `fix` | 오타·링크·버그 수정 |
| `docs` | 위키 또는 R&D 로그 변경 |
| `chore` | 빌드/설정/스타일 변경 |
| `refactor` | 문서 구조 재조정 |

예시:

```bash
git commit -m "docs(wiki): add behavioral cloning theory page"
git commit -m "feat(rnd): add Phase 2-A first training experiment log"
git commit -m "fix(wiki): correct broken link in carla-simulator.md"
```

### 2.5 푸시 + Pull Request 생성

```bash
git push -u origin wiki/add-bc-theory

# PR 생성
gh pr create \
  --title "docs(wiki): add behavioral cloning theory page" \
  --body "BC 이론 페이지 추가. 수식과 예시 코드 포함."
```

## 3. PR 리뷰 정책

| 항목 | 정책 |
|------|------|
| 최소 리뷰어 | 1명 (2인 팀 기준) |
| 자동 검사 | GitHub Actions의 mkdocs build 통과 필수 |
| 머지 방식 | Squash and Merge (히스토리 깔끔 유지) |
| 머지 후 브랜치 | 자동 삭제 |

## 4. 자동 배포

`main` 브랜치에 머지되면 GitHub Actions가 자동으로 사이트를 빌드하여 GitHub Pages에 배포합니다. 보통 머지 후 1~3분 이내에 [https://soongsantech.github.io](https://soongsantech.github.io)에 반영됩니다.

## 5. 충돌 해결

자주 발생하지 않지만, 동시에 같은 파일을 수정한 경우:

```bash
git checkout main
git pull origin main
git checkout your-branch
git rebase main
# 충돌 해결 후
git add .
git rebase --continue
git push -f origin your-branch
```

## 6. 자주 묻는 질문

??? question "로컬 미리보기에서는 잘 보이는데 배포 후 깨져요"
    절대 경로(`/...`)를 사용했는지 확인하세요. MkDocs는 상대 경로(`../`, `./`)를 권장합니다.

??? question "이미지가 안 보여요"
    이미지는 반드시 `docs/assets/img/` 하위에 두어야 합니다. 그 외 위치는 빌드에서 제외됩니다.

??? question "수식이 렌더링되지 않아요"
    `\(...\)` (인라인) 또는 `$$...$$` (블록)을 사용하세요. `$...$` (인라인)은 비활성화되어 있습니다.
