# songsh0906.github.io — 블로그 자동 작성 규칙

## 블로그 정보
- 플랫폼: **Jekyll + Chirpy 테마**
- 배포: GitHub Pages (`main` 브랜치 → `https://songsh0906.github.io`)
- 언어: 한국어 (`lang: ko`)
- 시간대: `Asia/Seoul`
- 테마 모드: **다크 전용** (Terminal 스타일)

## 디자인 컨셉
"Terminal / 터미널 레트로" — 모노스페이스 폰트, 앰버(#e8a24a) 액센트, 깊은 녹흑 배경.
- 폰트: JetBrains Mono / IBM Plex Mono
- 액센트 색: `#e8a24a` (amber)
- 사이트 제목 앞에 `$ ` 프롬프트, 포스트 제목 앞에 `> ` 프롬프트가 자동 붙음
- 커스텀 CSS 위치: `assets/css/jekyll-theme-chirpy.scss` 하단

## 글 작성 규칙

### 파일 저장 위치와 이름
- 경로: `_posts/`
- 파일명 형식: `YYYY-MM-DD-slug.md` (예: `2026-10-14-claude-automation.md`)
- 파일명의 slug 부분은 **영문 소문자 + 하이픈**을 권장 (한글도 허용되지만 URL 호환성을 위해 영문 선호)

### Front matter 템플릿
```yaml
---
title: "제목 — 소제목이 있으면 em dash 로 연결"
date: 2026-10-14 14:30:00 +0900
categories: [대분류, 소분류]
tags: [tag1, tag2, tag3]       # 소문자, 영문/한글 모두 OK
pin: false                      # 상단 고정 여부
math: false                     # KaTeX 수식 사용 시 true
mermaid: false                  # Mermaid 다이어그램 사용 시 true
image:
  path: /assets/img/posts/2026-10-14-cover.png   # (선택) 커버 이미지
  alt: 간단한 이미지 설명
---
```

### 글 톤과 스타일
- **반말이 아닌 '~한다' / '~했다' 체** (연구노트 느낌). 사용자가 특별히 지시하면 반말 or 존댓말로.
- 과장된 수사·이모지 금지. 담담하고 기록적인 문장.
- "결론부터 → 과정 → 삽질 포인트 → 다음에 할 것" 순서를 선호.
- 코드 블록에는 반드시 언어 지정 (`` ```python ``, `` ```sql `` 등) — Rouge 신택스 하이라이트 사용.
- 중요한 포인트는 `> 블록인용`으로 강조. (왼쪽 앰버 바가 자동으로 붙음)
- 인라인 `code`는 앰버 색으로 자동 렌더링되므로 적극 활용.

### 카테고리 체계 (현재)
- `[개발, 자동화]` — 워크플로우/도구 관련
- `[개발, 데이터]` — SQL/DB/성능
- `[개발, UI]` — 프론트/디자인
- `[기록]` — 그 외 노트/일지
새 카테고리가 필요하면 자유롭게 추가.

### 이미지
- 저장 위치: `assets/img/posts/`
- 파일명: `YYYY-MM-DD-설명.확장자`
- 마크다운: `![alt](/assets/img/posts/파일명.png)`
- 캡션 필요 시: `_italic_` 로 바로 아래 줄에 적음.

## 자동화 워크플로우

사용자가 주제를 던지면 다음 순서로 처리:

1. **주제 정리** — 사용자가 준 설명에서 핵심 메시지·독자·톤을 뽑는다.
2. **파일명 생성** — 오늘 날짜 + 영문 slug.
3. **드래프트 작성** — 위 front matter 템플릿 + 본문. **커밋 전 사용자에게 미리 보여주고 승인받는다.**
4. **승인 후** — `_posts/`에 저장 → `git add` → `git commit` → `git push origin main`.
5. **커밋 메시지 포맷**:
   ```
   post: <제목> 추가

   Co-Authored-By: Claude Opus 4.7 <noreply@anthropic.com>
   ```
   (수정 시 `post:` 대신 `fix:` / `tweak:` 사용)

## Git 설정
- Remote: `https://github.com/songsh0906/songsh0906.github.io`
- 로컬: `E:\깃블로그용 클로드\songsh0906.github.io`
- user.email: `songsh0906@naver.com`
- user.name: `songsh0906`

## 주의
- 민감 정보(토큰, 비밀번호, 내부 URL) 절대 커밋 금지. 포스트에 들어가면 반드시 마스킹.
- GitHub Pages 빌드가 끝나기까지 1~2분 소요. 푸시 직후 바로 확인하면 반영 안 되어 있을 수 있음.
- 테마 색을 바꾸고 싶으면 `assets/css/jekyll-theme-chirpy.scss` 상단의 `--link-color` 등을 수정.
