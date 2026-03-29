# Dark Presentation

Claude Code 스킬 — 프리미엄 다크 테마 HTML 프레젠테이션을 단일 파일로 생성합니다.

맥킨지/컨설팅 스타일의 슬라이드 덱을 키보드 네비게이션, 터치 지원, PDF 자동 변환과 함께 제공합니다.

## 미리보기

<table>
<tr>
<td><img src="https://github.com/user-attachments/assets/placeholder-title" width="400" alt="타이틀 슬라이드"></td>
<td><img src="https://github.com/user-attachments/assets/placeholder-content" width="400" alt="콘텐츠 슬라이드"></td>
</tr>
</table>

> 실제 사용 후 스크린샷으로 교체하세요.

## 주요 기능

- **단일 HTML 파일** — 빌드 없이 브라우저에서 바로 열림
- **다크 테마** — 검정 배경 + 따뜻한 크림 텍스트 + 골드/레드/그린 악센트
- **슬라이드 네비게이션** — 키보드 화살표, 터치 스와이프, 클릭 영역, 프로그레스 바
- **12종 컴포넌트** — 배지, 카드, 콜아웃, VS 블록, 통계 블록, 타임라인, 테이블 등
- **리빌 애니메이션** — 슬라이드 전환 시 순차 페이드인
- **Unsplash 배경** — 히어로 이미지 + 그라디언트 오버레이
- **필름 그레인 오버레이** — SVG 노이즈 텍스처로 프리미엄 질감
- **반응형** — 모바일/태블릿 + 인쇄 CSS 지원
- **PDF 자동 변환** — Playwright 캡처 + Pillow PDF 합성
- **한국어 우선 타이포그래피** — Noto Sans KR, Noto Serif KR, Bebas Neue, Cormorant Garamond

## 설치

```bash
# Claude Code 스킬 디렉토리에 클론
git clone https://github.com/pureivy/dark-presentation.git ~/.claude/skills/dark-presentation
```

또는 수동으로 복사:

```
~/.claude/skills/dark-presentation/
├── SKILL.md
├── README.md
└── references/
    ├── components.md
    └── navigation.md
```

## 사용법

Claude Code에서 다음과 같이 말하세요:

```
프레젠테이션 만들어줘
발표자료 만들어줘
HTML 슬라이드 덱
컨설팅 스타일 발표
특강 자료 만들어줘
```

스킬이 자동으로:
1. 주제, 대상 청중, 핵심 메시지를 파악
2. 슬라이드 구성안 제안 (10~16장)
3. 단일 HTML 파일 생성
4. PDF 자동 변환

## 출력 형식

| 형식 | 적합한 상황 |
|------|------------|
| **슬라이드 덱** (기본) | 발표, 강연, 특강, 회의 |
| **스크롤 리포트** | 보고서, 정책 문서, 전략 문서 |

## 디자인 시스템

### 색상

| 토큰 | 컬러 | 용도 |
|------|------|------|
| `--black` | `#0a0a0a` | 배경 |
| `--white` | `#f5f2eb` | 따뜻한 크림 텍스트 |
| `--gold` | `#d4b06a` | 주 악센트 |
| `--red-soft` | `#ef6050` | 위기 / 위험 |
| `--green` | `#3cc474` | 성공 / 긍정 |

### 타이포그래피

| 폰트 | 용도 |
|------|------|
| Bebas Neue | 라벨, 숫자, 임팩트 텍스트 |
| Cormorant Garamond | 영문 디스플레이 인용 |
| Noto Sans KR | 본문, 제목 |
| Noto Serif KR | 한국어 인용 |

### 컴포넌트

`badge` · `card` · `callout` · `vs-block` · `stat-block` · `list-item` · `timeline-row` · `comp-table` · `corner-mark` · `vertical-text` · `divider`

## PDF 변환

Python `playwright`와 `Pillow`가 필요합니다:

```bash
pip install playwright Pillow
python -m playwright install chromium
```

HTML 생성 후 PDF 변환이 자동으로 실행됩니다.

## 파일 구조

```
SKILL.md                 — 메인 스킬 (디자인 시스템, 생성 프로세스, 체크리스트)
references/
  components.md          — 12종 컴포넌트 CSS + HTML 패턴
  navigation.md          — 슬라이드 JS, HTML 골격, Unsplash 이미지 ID
```

## 라이선스

MIT
