---
name: dark-presentation
description: "프리미엄 다크 테마 HTML 프레젠테이션을 단일 파일로 생성합니다. 맥킨지/컨설팅 스타일의 슬라이드 덱 또는 스크롤 리포트를 만들 때 사용하세요. 트리거: 프레젠테이션 만들어줘, 발표자료 만들어줘, HTML 슬라이드, 다크 테마 발표, 슬라이드 덱, 특강 자료, 보고서 프레젠테이션, presentation, slide deck, dark theme slides, 컨설팅 스타일 발표, 강의자료, 리포트 HTML"
---

# Dark Presentation — 프리미엄 단일파일 HTML 프레젠테이션 생성기

주제와 콘텐츠를 받아 **단일 HTML 파일**로 된 프리미엄 다크 테마 프레젠테이션을 생성한다. 외부 의존성 없이 브라우저에서 바로 열 수 있다.

## 출력 형식 선택

사용자의 요구에 따라 두 가지 형식 중 하나를 선택한다:

| 형식 | 특징 | 적합한 상황 |
|------|------|------------|
| **슬라이드 덱** | 풀스크린, 키보드/터치 네비게이션 | 발표, 강연, 특강, 회의 |
| **스크롤 리포트** | 긴 페이지 스크롤, 사이드 네비게이션 | 보고서, 정책 문서, 전략 문서 |

기본값은 **슬라이드 덱**이다. 사용자가 "보고서", "리포트", "문서" 등을 언급하면 스크롤 리포트를 제안한다.

## 핵심 원칙

1. **단일 파일**: CSS, JS 모두 인라인. 외부 의존성은 Google Fonts CDN만 사용
2. **다크 테마**: 검정 배경 + 따뜻한 크림 텍스트 + 골드 악센트
3. **한국어 중심**: Noto Sans KR / Noto Serif KR 기본, 영문 디스플레이는 Bebas Neue / Cormorant Garamond
4. **Unsplash 배경**: 각 슬라이드에 주제에 맞는 Unsplash 이미지 URL 사용
5. **반응형**: 모바일/태블릿 대응, 인쇄 지원
6. **10~16장**: 슬라이드는 보통 10~16장이 적당하다

## 디자인 시스템

### 색상 (CSS Variables)

```css
:root {
  --black: #0a0a0a;
  --charcoal: #141414;
  --dark: #1a1a1a;
  --mid: #2a2a2a;
  --border: #333;
  --muted: #888;
  --secondary: #bbb;
  --light: #e0dcd4;
  --white: #f5f2eb;      /* 따뜻한 크림 화이트 */
  --cream: #ede8dc;
  --gold: #d4b06a;        /* 주 악센트 */
  --gold-bright: #e8c88a;
  --gold-dim: rgba(200,165,92,0.12);
  --red: #c0392b;         /* 위기/위험 */
  --red-soft: #ef6050;
  --red-dim: rgba(192,57,43,0.15);
  --green: #3cc474;       /* 성공/긍정 */
  --green-dim: rgba(39,174,96,0.12);
  --blue: #2980b9;        /* 보조 */
}
```

### 타이포그래피

| 용도 | 폰트 | 클래스 |
|------|------|--------|
| 디스플레이 (영문 인용) | Cormorant Garamond | `.font-display` |
| 임팩트 레이블/숫자 | Bebas Neue | `.font-impact` |
| 본문 | Noto Sans KR | `.font-body` |
| 한국어 인용 | Noto Serif KR | `.font-serif` |

Google Fonts 로드:
```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Bebas+Neue&family=Noto+Sans+KR:wght@300;400;500;700;900&family=Noto+Serif+KR:wght@400;600;700&display=swap" rel="stylesheet">
```

### 텍스트 스타일

- `.mega`: 메인 타이틀 — `font-weight:900; font-size:clamp(36px,4.5vw,64px)`
- `.title`: 섹션 제목 — `font-weight:700; font-size:clamp(24px,3vw,44px)`
- `.subtitle`: 부제목 — `font-size:clamp(16px,1.6vw,22px); color:var(--light)`
- `.label`: 라벨 — Bebas Neue, 13px, letter-spacing:4px, 골드, uppercase
- `.big-num`: 큰 숫자 — Bebas Neue, `font-size:clamp(56px,7vw,108px)`, 골드
- `.quote-text`: 한국어 인용 — Noto Serif KR, 600, `font-size:clamp(20px,2.4vw,36px)`
- `.quote-en`: 영문 인용 — Cormorant Garamond, 이탤릭

## 컴포넌트 라이브러리

전체 CSS와 사용 예시는 [references/components.md](references/components.md)를 읽어라.

핵심 컴포넌트 목록:

| 컴포넌트 | 용도 |
|----------|------|
| `badge` | 섹션 태그 (골드/레드/그린 테두리) |
| `divider` | 골드 구분선 (60px) |
| `card` | 카드 (반투명 배경 + 상단 컬러 바) |
| `callout` | 강조 블록 (좌측 3px 테두리) |
| `vs-block` | 대비 레이아웃 (A vs B) |
| `stat-block` | 통계 수치 표시 |
| `list-item` + `dot` | 골드 도트 리스트 |
| `timeline-row` | 연도별 타임라인 |
| `comp-table` | 비교 테이블 |
| `corner-mark` | 장식용 L자 코너 |
| `vertical-text` | 세로 워터마크 텍스트 |

## 슬라이드 구성 패턴

### 1. 타이틀 슬라이드 (필수)
- 히어로 배경 이미지 + 코너 마크
- `.label` 조직명/행사명
- `.mega` 메인 타이틀 (골드 강조)
- `.divider.center`
- `.font-display` 부제 (이탤릭)
- 날짜

### 2. 데이터/위기 슬라이드
- `.badge.red` + `.title` (레드 강조)
- `.grid-3` 또는 `.grid-4`에 `.card.red-top`
- 통계 수치는 `.big-num.red`

### 3. VS 대비 슬라이드
- `.vs-block`: 좌측 `.vs-side` + `.vs-divider` (VS) + 우측 `.vs-side`
- 대조되는 두 개념 비교

### 4. 인물/인용 슬라이드
- 중앙 정렬 `.container.center`
- `.quote-text` 또는 `.quote-en`
- `.divider.center`
- 하단 `.grid-2` 카드로 세부 설명

### 5. 리스트/원칙 슬라이드
- `.grid-2`에 번호 카드 배치
- 각 카드에 `.font-impact` 번호 + 제목 + 설명

### 6. 프로세스/흐름 슬라이드
- 카드들을 화살표(→)로 연결
- 또는 `.timeline-row` 사용

### 7. 마무리 슬라이드 (필수)
- 히어로 배경 + 코너 마크
- 핵심 메시지 `.mega`
- `.divider.center`
- 마무리 인용 `.font-display`
- 연락처/조직 정보

## 슬라이드 JS 시스템

슬라이드 덱은 반드시 아래 JS를 `</body>` 직전에 포함한다. [references/navigation.md](references/navigation.md)에서 전체 코드를 확인하라.

기능:
- 키보드: ← → ↑ ↓ Space PageUp PageDown Home End
- 터치: 좌우 스와이프 (50px 이상)
- 클릭: 화면 우측 75% = 다음, 좌측 25% = 이전
- 상단 프로그레스 바
- 우측 하단 슬라이드 번호 (01 / 14)
- 좌측 하단 네비게이션 힌트

## 리빌 애니메이션

각 슬라이드 안의 요소에 `.reveal` 클래스를 부여하면 슬라이드가 활성화될 때 아래에서 위로 페이드인한다.
지연 시간은 `.d1`(0.1s) ~ `.d6`(0.8s)으로 순차적으로 나타나도록 한다.

```html
<div class="reveal d1"><div class="badge">TITLE</div></div>
<div class="reveal d2"><h2 class="title">...</h2></div>
<div class="reveal d3"><!-- content --></div>
```

## 그레인 오버레이

body::after에 SVG 기반 fractalNoise 텍스처를 오버레이한다. 이것이 프리미엄 필름 느낌을 준다.

## Unsplash 이미지 URL 패턴

주제에 맞는 Unsplash 이미지를 사용한다:
```
https://images.unsplash.com/photo-{ID}?auto=format&fit=crop&w=1920&q=80
```

히어로 배경에는 반드시 오버레이 그라디언트를 적용한다:
- `.hero-bg` — 기본 135도 그라디언트 (0.92 → 0.75 → 0.88)
- `.hero-bg.dark-overlay` — 위아래 어두운 (0.94 → 0.8 → 0.92)
- `.hero-bg.left-overlay` — 좌측 어두운 (0.95 → 0.9 → 0.6)
- `.hero-bg.bottom-overlay` — 하단 어두운 (0.96 → 0.82 → 0.65)

## 생성 프로세스

1. 사용자에게 **주제**, **대상 청중**, **핵심 메시지**를 파악한다
2. 형식(슬라이드 덱/스크롤 리포트)을 결정한다
3. 슬라이드 구성안을 먼저 간략히 공유한다 (10~16장)
4. [references/components.md](references/components.md)와 [references/navigation.md](references/navigation.md)를 읽는다
5. 단일 HTML 파일로 생성한다
6. `open` 명령으로 브라우저에서 열어 확인한다
7. HTML 생성 후 **항상 PDF도 함께 생성**한다 (아래 PDF 변환 섹션 참조)

## PDF 변환

HTML 프레젠테이션을 생성한 뒤, Playwright로 각 슬라이드를 1920x1080 스크린샷 캡처하고 Pillow로 PDF를 합성한다. HTML과 동일한 디렉토리에 같은 이름의 `.pdf` 파일로 저장한다.

### 변환 스크립트

HTML 파일 경로를 `html_path`에, PDF 출력 경로를 `pdf_path`에 넣고 아래 Python 스크립트를 실행한다:

```python
from playwright.sync_api import sync_playwright
from PIL import Image
import os, io

html_path = "/path/to/presentation.html"
pdf_path = html_path.rsplit(".", 1)[0] + ".pdf"

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page(viewport={"width": 1920, "height": 1080})
    page.goto(f"file://{html_path}")
    page.wait_for_timeout(1000)

    total = page.evaluate("document.querySelectorAll('.slide').length")
    images = []

    for i in range(total):
        page.evaluate(f"""
            document.querySelectorAll('.slide').forEach(s => s.classList.remove('active'));
            document.querySelectorAll('.slide')[{i}].classList.add('active');
        """)
        page.wait_for_timeout(800)
        screenshot = page.screenshot(type="png")
        img = Image.open(io.BytesIO(screenshot)).convert("RGB")
        images.append(img)

    browser.close()

if images:
    images[0].save(pdf_path, save_all=True, append_images=images[1:], resolution=150)
```

### 핵심 포인트

- **뷰포트**: 1920x1080 (16:9 프레젠테이션 비율)
- **대기 시간**: 슬라이드 전환 후 800ms 대기 (reveal 애니메이션 완료)
- **해상도**: 150 DPI (파일 크기와 품질의 균형)
- **의존성**: `playwright` + `Pillow` (Python)
- **출력**: HTML과 같은 디렉토리, 같은 파일명에 `.pdf` 확장자

## 품질 체크리스트

- [ ] 모든 CSS가 `<style>` 안에 있는가?
- [ ] 모든 JS가 `<script>` 안에 있는가?
- [ ] Google Fonts CDN 링크가 포함되었는가?
- [ ] 그레인 오버레이가 적용되었는가?
- [ ] 각 슬라이드에 `.reveal` 애니메이션이 있는가?
- [ ] 히어로 배경에 오버레이 그라디언트가 있는가?
- [ ] 프로그레스 바와 슬라이드 번호가 작동하는가?
- [ ] 반응형 (768px 미만) 스타일이 있는가?
- [ ] 인쇄 스타일이 있는가?
- [ ] `lang="ko"`가 설정되었는가?
- [ ] PDF 파일이 HTML과 같은 디렉토리에 생성되었는가?
- [ ] PDF의 모든 슬라이드가 정상적으로 캡처되었는가?
