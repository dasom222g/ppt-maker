# ppt-maker

웹 기반 강의 슬라이드를 생성하는 프로젝트. 순수 HTML/CSS/JS 단일 파일로 프레젠테이션을 만들며, Claude의 `web-slide-maker` 스킬로 자동화한다.

## 프로젝트 구조

```
slides/           ← 완성된 슬라이드 HTML 결과물
docs/             ← 리서치 노트, 디자인 룰 참고 문서
prompt-source/    ← 슬라이드 생성에 사용된 프롬프트 원본
template-source/  ← 디자인 레퍼런스 이미지 (슬라이드 패턴 참고용)
lecture-source/   ← 강의 원본 자료 (PDF 등) — gitignore 처리, GitHub 미업로드
.claude/          ← Claude 스킬 정의
  └── skill-web-slide-maker/
        ├── SKILL.md              ← 슬라이드 생성 워크플로우
        ├── assets/base-template.html   ← 모든 슬라이드의 베이스 CSS+JS
        └── references/
              ├── design-rules.md ← 색상 토큰, 타이포그래피, 스페이싱
              └── patterns.md     ← 14가지 슬라이드 패턴 HTML 구조
```

## 슬라이드 생성 규칙

- **출력 경로**: 반드시 `slides/` 폴더 안에 저장 — 루트에 직접 두지 않는다
- **파일명**: `{강의명}-slides.html` (소문자, 하이픈, 공백 없음)
- **단일 파일**: 모든 CSS·JS·콘텐츠를 하나의 `.html` 파일에 인라인으로 포함
- **베이스 템플릿**: 항상 `assets/base-template.html`을 시작점으로 사용
- **강의 원본(PDF 등)**: `lecture-source/`에 보관하되 Git에 올리지 않는다

## 슬라이드 생성 워크플로우 (요약)

1. 강의 자료 분석 → 핵심 메시지 추출
2. 슬라이드 구성 계획 작성 → **사용자 확인 후** 구현 시작
3. `slides/` 폴더에 HTML 파일 저장

전체 워크플로우는 `.claude/skill-web-slide-maker/SKILL.md` 참고.

## 디자인 시스템

- **다크 모드** 전용: 배경 `#0d1117`, 주요 강조색 teal `#2DD4BF`
- **폰트**: Pretendard (본문) + GmarketSans (디스플레이)
- **네비게이션**: 키보드(← →, Space), 터치 스와이프, 하단 dot nav
- 색상·타이포·컴포넌트 클래스 전체 목록: `docs/figma-design-rules.md`

## Git 규칙

- `lecture-source/` 는 `.gitignore` 처리 — 절대 커밋하지 않는다
- 커밋은 작업 단위별로 분리: 구조 변경 / 슬라이드 결과물 / 설정 업데이트
