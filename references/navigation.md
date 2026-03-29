# 슬라이드 네비게이션 시스템

## 전체 HTML 골격

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>프레젠테이션 제목</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Bebas+Neue&family=Noto+Sans+KR:wght@300;400;500;700;900&family=Noto+Serif+KR:wght@400;600;700&display=swap" rel="stylesheet">
<style>
/* === 여기에 전체 CSS 삽입 === */
</style>
</head>
<body>

<div class="progress" id="progress"></div>
<div class="slide-num" id="slideNum"></div>
<div class="nav-hint">← → 키 이동</div>

<div class="deck" id="deck">

<!-- 슬라이드 1 -->
<div class="slide" data-slide="1">
  <!-- content -->
</div>

<!-- 슬라이드 2 -->
<div class="slide" data-slide="2">
  <!-- content -->
</div>

<!-- ... 슬라이드 반복 ... -->

</div><!-- end deck -->

<script>
/* === 여기에 네비게이션 JS 삽입 === */
</script>

</body>
</html>
```

## 슬라이드 시스템 CSS

```css
/* ===== SLIDE SYSTEM ===== */
.deck { position: relative; width: 100vw; height: 100vh; }

.slide {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.7s cubic-bezier(0.4,0,0.2,1), visibility 0s 0.7s;
}

.slide.active {
  opacity: 1;
  visibility: visible;
  transition: opacity 0.7s cubic-bezier(0.4,0,0.2,1), visibility 0s;
}

.slide.active .reveal {
  opacity: 1;
  transform: translateY(0);
}

/* ===== REVEAL ANIMATION ===== */
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.reveal.d1 { transition-delay: 0.1s; }
.reveal.d2 { transition-delay: 0.2s; }
.reveal.d3 { transition-delay: 0.35s; }
.reveal.d4 { transition-delay: 0.5s; }
.reveal.d5 { transition-delay: 0.65s; }
.reveal.d6 { transition-delay: 0.8s; }

/* ===== PROGRESS BAR ===== */
.progress {
  position: fixed; top: 0; left: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--gold), var(--gold-bright));
  z-index: 1000;
  transition: width 0.5s ease;
}

/* ===== SLIDE NUMBER ===== */
.slide-num {
  position: fixed; bottom: 28px; right: 36px;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 14px;
  letter-spacing: 3px;
  color: var(--muted);
  z-index: 1000;
}

/* ===== NAV HINT ===== */
.nav-hint {
  position: fixed; bottom: 28px; left: 36px;
  font-family: 'Noto Sans KR', sans-serif;
  font-size: 11px;
  color: var(--muted);
  opacity: 0.4;
  z-index: 1000;
}
```

## 히어로 배경 CSS

```css
/* ===== HERO IMAGES ===== */
.hero-bg {
  position: absolute; inset: 0;
  background-size: cover;
  background-position: center;
  z-index: 0;
}

.hero-bg::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(10,10,10,0.92) 0%, rgba(10,10,10,0.75) 50%, rgba(10,10,10,0.88) 100%);
}

.hero-bg.dark-overlay::after {
  background: linear-gradient(to bottom, rgba(10,10,10,0.94) 0%, rgba(10,10,10,0.8) 40%, rgba(10,10,10,0.92) 100%);
}

.hero-bg.left-overlay::after {
  background: linear-gradient(to right, rgba(10,10,10,0.95) 0%, rgba(10,10,10,0.9) 45%, rgba(10,10,10,0.6) 100%);
}

.hero-bg.bottom-overlay::after {
  background: linear-gradient(to top, rgba(10,10,10,0.96) 0%, rgba(10,10,10,0.82) 40%, rgba(10,10,10,0.65) 100%);
}

/* ===== SLIDE INNER ===== */
.slide-inner {
  position: relative;
  z-index: 1;
  padding: 60px 80px;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow-y: auto;
}

.slide-inner.pad-lg { padding: 80px 100px; }
```

## 그레인 오버레이 CSS

```css
body::after {
  content: '';
  position: fixed;
  inset: 0;
  z-index: 9999;
  pointer-events: none;
  opacity: 0.035;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
  background-repeat: repeat;
  background-size: 200px;
}
```

## 바디 기본 CSS

```css
* { margin:0; padding:0; box-sizing:border-box; }

body {
  background: var(--black);
  color: var(--white);
  overflow: hidden;
  height: 100vh;
  width: 100vw;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

## 인쇄 CSS

```css
@media print {
  .slide {
    position: relative;
    opacity: 1;
    visibility: visible;
    page-break-after: always;
    min-height: 100vh;
  }
  .progress, .slide-num, .nav-hint { display: none; }
  .hero-bg { position: relative; }
}
```

## 네비게이션 JavaScript

이 스크립트를 `</body>` 직전에 넣는다. 변경하지 않고 그대로 사용한다.

```javascript
(function(){
  const slides = document.querySelectorAll('.slide');
  const progress = document.getElementById('progress');
  const slideNum = document.getElementById('slideNum');
  let cur = 0;
  const total = slides.length;

  function go(i) {
    if (i < 0 || i >= total) return;
    slides[cur].classList.remove('active');
    cur = i;
    slides[cur].classList.add('active');
    progress.style.width = ((cur + 1) / total * 100) + '%';
    slideNum.textContent = String(cur + 1).padStart(2, '0') + ' / ' + String(total).padStart(2, '0');
  }

  document.addEventListener('keydown', function(e) {
    switch(e.key) {
      case 'ArrowRight': case 'ArrowDown': case ' ': case 'PageDown':
        e.preventDefault(); go(cur + 1); break;
      case 'ArrowLeft': case 'ArrowUp': case 'PageUp':
        e.preventDefault(); go(cur - 1); break;
      case 'Home': e.preventDefault(); go(0); break;
      case 'End': e.preventDefault(); go(total - 1); break;
    }
  });

  let tx = 0;
  document.addEventListener('touchstart', function(e){ tx = e.touches[0].clientX; });
  document.addEventListener('touchend', function(e){
    const d = tx - e.changedTouches[0].clientX;
    if (Math.abs(d) > 50) { d > 0 ? go(cur+1) : go(cur-1); }
  });

  document.addEventListener('click', function(e){
    const w = window.innerWidth;
    if (e.clientX > w * 0.75) go(cur+1);
    else if (e.clientX < w * 0.25) go(cur-1);
  });

  go(0);
})();
```

## 자주 쓰는 Unsplash 이미지 ID (주제별)

사용 형식: `https://images.unsplash.com/photo-{ID}?auto=format&fit=crop&w=1920&q=80`

### 비즈니스/경영
- `photo-1504384308090-c894fdcc538d` — 오피스 회의
- `photo-1552664730-d307ca884978` — 팀워크 회의
- `photo-1521737604893-d14cc237f11d` — 협업

### 기술/혁신
- `photo-1451187580459-43490279c0fa` — 지구와 기술
- `photo-1677442136019-21780ecad995` — AI/디지털
- `photo-1517694712202-14dd9538aa97` — 코딩

### 금융/경제
- `photo-1611974789855-9c2a0a7236a3` — 차트/주식
- `photo-1554224155-6726b3ff858f` — 금융 문서
- `photo-1454165804606-c3d57bc86b40` — 비즈니스 미팅

### 자연/영감
- `photo-1470071459604-3b5ec3a7fe05` — 산과 안개
- `photo-1507003211169-0a1dd7228f2d` — 포트레이트 (인물)

### 도시/한국
- `photo-1546874177-9e664107314e` — 서울 야경

배경 이미지를 선택할 때 슬라이드의 주제와 톤에 맞는 것을 고른다. 밝은 이미지도 오버레이가 어둡게 처리하므로 문제없다.
