# 컴포넌트 라이브러리 — CSS & HTML 패턴

이 문서는 프레젠테이션에서 사용하는 모든 UI 컴포넌트의 CSS 정의와 HTML 사용 예시를 담고 있다.

## 목차

1. [레이아웃](#레이아웃)
2. [배지 (Badge)](#배지-badge)
3. [구분선 (Divider)](#구분선-divider)
4. [카드 (Card)](#카드-card)
5. [콜아웃 (Callout)](#콜아웃-callout)
6. [VS 블록](#vs-블록)
7. [리스트 아이템](#리스트-아이템)
8. [통계 블록 (Stat Block)](#통계-블록)
9. [타임라인](#타임라인)
10. [테이블](#테이블)
11. [장식 요소](#장식-요소)
12. [유틸리티 클래스](#유틸리티-클래스)

---

## 레이아웃

### CSS

```css
.container { max-width: 1100px; width: 100%; }
.container.narrow { max-width: 800px; }
.container.center { margin: 0 auto; text-align: center; }

.flex { display: flex; }
.flex-col { flex-direction: column; }
.gap-sm { gap: 12px; }
.gap-md { gap: 20px; }
.gap-lg { gap: 32px; }
.gap-xl { gap: 48px; }
.items-center { align-items: center; }
.justify-center { justify-content: center; }
.text-center { text-align: center; }

.grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
.grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 20px; }
.grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }
```

### 반응형

```css
@media (max-width: 768px) {
  .slide-inner { padding: 40px 28px; }
  .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
  .hide-mobile { display: none; }
  .vs-block { flex-direction: column; }
  .vs-block .vs-divider { width: 100%; height: 40px; }
}
```

---

## 배지 (Badge)

섹션의 카테고리/태그를 표시한다.

### CSS

```css
.badge {
  display: inline-block;
  padding: 5px 16px;
  border: 1px solid var(--gold);
  border-radius: 0;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 12px;
  letter-spacing: 3px;
  color: var(--gold);
}
.badge.red { border-color: var(--red-soft); color: var(--red-soft); }
.badge.green { border-color: var(--green); color: var(--green); }
```

### HTML

```html
<div class="badge">ENTREPRENEURSHIP</div>
<div class="badge red">위기의 시대</div>
<div class="badge green">경북경제진흥원</div>
```

---

## 구분선 (Divider)

골드 색상의 짧은 수평선으로 섹션을 구분한다.

### CSS

```css
.divider {
  width: 60px;
  height: 1px;
  background: var(--gold);
  margin: 16px 0;
}
.divider.center { margin: 16px auto; }
```

### HTML

```html
<div class="divider"></div>
<div class="divider center"></div>
```

---

## 카드 (Card)

정보를 담는 반투명 카드. 상단에 컬러 바를 넣어 강조할 수 있다.

### CSS

```css
.card {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.06);
  padding: 28px;
  position: relative;
  overflow: hidden;
}
.card::before {
  content: '';
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 2px;
  background: transparent;
}
.card.gold-top::before { background: var(--gold); }
.card.red-top::before { background: var(--red-soft); }
.card.green-top::before { background: var(--green); }

.card-label {
  font-family: 'Bebas Neue', sans-serif;
  font-size: 11px;
  letter-spacing: 3px;
  color: var(--muted);
  margin-bottom: 10px;
}
.card-value {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(28px, 3vw, 44px);
  color: var(--gold);
  letter-spacing: 1px;
}
.card-value.red { color: var(--red-soft); }
.card-value.green { color: var(--green); }
.card-desc {
  font-size: 15px;
  color: var(--light);
  line-height: 1.6;
  margin-top: 6px;
}
```

### HTML — 기본 카드

```html
<div class="card gold-top" style="padding:24px;">
  <div class="card-label">CATEGORY</div>
  <p class="gold fw-700" style="font-size:16px; margin:8px 0;">제목</p>
  <div class="divider" style="margin:10px 0;"></div>
  <p style="font-size:15px; color:var(--light); line-height:1.7;">
    내용 텍스트
  </p>
</div>
```

### HTML — 수치 카드

```html
<div class="card red-top" style="padding:20px;">
  <div class="card-label">지표명</div>
  <div class="card-value red">-45%</div>
  <div class="card-desc">설명 텍스트</div>
</div>
```

### HTML — 번호 카드 (원칙/단계)

```html
<div class="card gold-top" style="padding:20px;">
  <div style="display:flex; align-items:center; gap:16px;">
    <div class="font-impact" style="font-size:36px; color:var(--gold); opacity:0.3;">01</div>
    <div>
      <p class="gold fw-700" style="font-size:16px;">원칙 제목</p>
      <p style="font-size:14px; color:var(--secondary); margin-top:2px;">설명</p>
    </div>
  </div>
</div>
```

---

## 콜아웃 (Callout)

핵심 메시지를 강조하는 블록. 좌측에 컬러 테두리가 있다.

### CSS

```css
.callout {
  border-left: 3px solid var(--gold);
  padding: 18px 26px;
  background: var(--gold-dim);
  font-size: 17px;
  color: var(--white);
  line-height: 1.65;
}
.callout.red { border-color: var(--red-soft); background: var(--red-dim); }
.callout.green { border-color: var(--green); background: var(--green-dim); }
```

### HTML

```html
<div class="callout">
  <strong class="gold" style="font-size:18px;">핵심 메시지</strong><br>
  <span style="font-size:16px;">부연 설명 텍스트</span>
</div>

<div class="callout red">
  <strong class="red">경고 메시지</strong><br>
  위험 상황에 대한 설명
</div>

<div class="callout green">
  <strong class="green">긍정적 메시지</strong><br>
  성과나 기회에 대한 설명
</div>
```

---

## VS 블록

두 개념을 나란히 대비하는 레이아웃.

### CSS

```css
.vs-block {
  display: flex;
  align-items: stretch;
  gap: 0;
}
.vs-block .vs-side {
  flex: 1;
  padding: 24px;
}
.vs-block .vs-divider {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 56px;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 20px;
  letter-spacing: 2px;
  color: var(--gold);
}
```

### HTML

```html
<div class="vs-block">
  <div class="vs-side card red-top" style="text-align:center;">
    <p class="red fw-700" style="font-size:18px; margin-bottom:8px;">개념 A</p>
    <p style="font-size:15px; color:var(--light); line-height:1.7;">설명</p>
  </div>
  <div class="vs-divider">VS</div>
  <div class="vs-side card gold-top" style="text-align:center;">
    <p class="gold fw-700" style="font-size:18px; margin-bottom:8px;">개념 B</p>
    <p style="font-size:15px; color:var(--light); line-height:1.7;">설명</p>
  </div>
</div>
```

---

## 리스트 아이템

골드/레드/그린 도트가 있는 리스트.

### CSS

```css
.list-item {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  padding: 11px 0;
  border-bottom: 1px solid rgba(255,255,255,0.04);
  font-size: 17px;
  color: var(--white);
  line-height: 1.55;
}
.list-item:last-child { border-bottom: none; }

.dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--gold);
  margin-top: 8px;
  flex-shrink: 0;
}
.dot.red { background: var(--red-soft); }
.dot.green { background: var(--green); }
```

### HTML

```html
<div class="list-item"><span class="dot"></span><span><strong class="gold">키워드</strong> — 설명 텍스트</span></div>
<div class="list-item"><span class="dot red"></span><span><strong class="red">위험 요소</strong> — 설명</span></div>
<div class="list-item"><span class="dot green"></span><span><strong class="green">성과</strong> — 설명</span></div>
```

---

## 통계 블록

중앙 정렬된 큰 숫자 + 라벨.

### CSS

```css
.stat-block { text-align: center; }
.stat-num {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(32px, 4vw, 56px);
  color: var(--gold);
  letter-spacing: 1px;
  line-height: 1;
}
.stat-num.red { color: var(--red-soft); }
.stat-num.green { color: var(--green); }
.stat-label {
  font-size: 12px;
  color: var(--muted);
  margin-top: 6px;
  letter-spacing: 0.5px;
}
```

### HTML

```html
<div class="stat-block">
  <div class="stat-num">2,847</div>
  <div class="stat-label">참여 기업 수</div>
</div>
```

---

## 타임라인

연도별 이벤트를 세로로 나열한다.

### CSS

```css
.timeline-row {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  margin-bottom: 14px;
}
.timeline-year {
  font-family: 'Bebas Neue', sans-serif;
  font-size: 15px;
  color: var(--gold);
  min-width: 56px;
  text-align: right;
  letter-spacing: 1px;
  margin-top: 2px;
}
.timeline-line {
  width: 1px;
  min-height: 20px;
  background: var(--gold);
  opacity: 0.3;
  margin-top: 6px;
}
.timeline-text {
  font-size: 16px;
  color: var(--white);
  line-height: 1.55;
}
```

### HTML

```html
<div class="timeline-row">
  <div class="timeline-year">1983</div>
  <div class="timeline-line"></div>
  <div class="timeline-text">삼성 반도체 사업 선언 — <strong class="gold">도쿄 선언</strong></div>
</div>
<div class="timeline-row">
  <div class="timeline-year">2007</div>
  <div class="timeline-line"></div>
  <div class="timeline-text">iPhone 출시 — <strong class="gold">모바일 혁명</strong>의 시작</div>
</div>
```

---

## 테이블

비교 데이터를 표로 보여준다.

### CSS

```css
.comp-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
.comp-table th {
  padding: 12px 14px;
  text-align: left;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 13px;
  letter-spacing: 2px;
  color: var(--gold);
  border-bottom: 1px solid var(--gold);
  font-weight: 400;
}
.comp-table td {
  padding: 13px 14px;
  border-bottom: 1px solid rgba(255,255,255,0.06);
  color: var(--light);
  line-height: 1.5;
  vertical-align: top;
  font-size: 14px;
}
```

### HTML

```html
<table class="comp-table">
  <thead>
    <tr>
      <th>항목</th>
      <th>AS-IS</th>
      <th>TO-BE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>생산성</td>
      <td class="red">낮음</td>
      <td class="green">높음</td>
    </tr>
  </tbody>
</table>
```

---

## 장식 요소

### 코너 마크

타이틀/마무리 슬라이드에 사용하는 L자 코너 장식.

```css
.corner-mark {
  position: absolute;
  width: 40px; height: 40px;
  border: 1px solid rgba(200,165,92,0.15);
  z-index: 2;
}
.corner-mark.tl { top: 24px; left: 24px; border-right: none; border-bottom: none; }
.corner-mark.br { bottom: 24px; right: 24px; border-left: none; border-top: none; }
```

```html
<div class="corner-mark tl"></div>
<div class="corner-mark br"></div>
```

### 세로 워터마크

우측에 세로로 표시되는 조직명 등.

```css
.vertical-text {
  position: absolute;
  right: 36px;
  top: 50%;
  transform: translateY(-50%) rotate(90deg);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 11px;
  letter-spacing: 4px;
  color: rgba(255,255,255,0.08);
  white-space: nowrap;
  z-index: 2;
}
```

```html
<div class="vertical-text">ORGANIZATION NAME 2026</div>
```

### 출처 태그

```css
.src {
  display: inline-block;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 10px;
  letter-spacing: 1.5px;
  color: var(--muted);
  background: rgba(255,255,255,0.04);
  padding: 2px 8px;
  border-radius: 2px;
  margin-left: 4px;
  vertical-align: middle;
}
```

```html
<span class="src">McKinsey 2025</span>
```

---

## 유틸리티 클래스

```css
.gold { color: var(--gold); }
.red { color: var(--red-soft); }
.green { color: var(--green); }
.light { color: var(--light); }
.muted { color: var(--muted); }
.fw-900 { font-weight: 900; }
.fw-700 { font-weight: 700; }
.fw-300 { font-weight: 300; }
```

---

## 프로세스 플로우 (화살표 연결)

카드를 수평으로 배치하고 사이에 화살표를 넣는 패턴.

```html
<div style="display:flex; align-items:center; justify-content:center; gap:0; flex-wrap:wrap;">
  <div class="card green-top" style="flex:1; min-width:200px; text-align:center; padding:28px;">
    <div style="font-size:28px; margin-bottom:8px; opacity:0.5;">&#x1F3AF;</div>
    <p class="green fw-700" style="font-size:18px;">단계 1</p>
    <p style="font-size:14px; color:var(--secondary);">설명</p>
  </div>
  <div style="font-family:'Bebas Neue',sans-serif; font-size:28px; color:var(--green); padding:0 12px;">→</div>
  <div class="card green-top" style="flex:1; min-width:200px; text-align:center; padding:28px;">
    <div style="font-size:28px; margin-bottom:8px; opacity:0.5;">&#x1F4CB;</div>
    <p class="green fw-700" style="font-size:18px;">단계 2</p>
    <p style="font-size:14px; color:var(--secondary);">설명</p>
  </div>
  <div style="font-family:'Bebas Neue',sans-serif; font-size:28px; color:var(--green); padding:0 12px;">→</div>
  <div class="card green-top" style="flex:1; min-width:200px; text-align:center; padding:28px;">
    <div style="font-size:28px; margin-bottom:8px; opacity:0.5;">&#x1F91D;</div>
    <p class="green fw-700" style="font-size:18px;">단계 3</p>
    <p style="font-size:14px; color:var(--secondary);">설명</p>
  </div>
</div>
```

---

## 이모지 패턴

카드나 통계 블록 상단에 이모지를 장식으로 사용할 때:

```html
<div style="font-size:36px; margin-bottom:12px; opacity:0.6;">&#x1F3CB;</div>
```

- `opacity:0.5~0.6`으로 은은하게 처리
- HTML entity 형식 사용 (&#x1F3AF; 등)
- 콘텐츠의 성격을 시각적으로 표현하되 과하지 않게

---

## 슬라이드 구조 기본 패턴

```html
<div class="slide" data-slide="N">
  <!-- 배경 -->
  <div class="hero-bg dark-overlay" style="background-image:url('UNSPLASH_URL');"></div>

  <!-- 장식 (선택) -->
  <div class="corner-mark tl"></div>
  <div class="corner-mark br"></div>

  <!-- 컨텐츠 -->
  <div class="slide-inner">
    <div class="container">
      <div class="reveal d1"><!-- 배지/라벨 --></div>
      <div class="reveal d2"><!-- 제목 --></div>
      <div class="reveal d3"><!-- 본문/그리드 --></div>
      <div class="reveal d4"><!-- 추가 콘텐츠 --></div>
      <div class="reveal d5"><!-- 콜아웃/마무리 --></div>
    </div>
  </div>
</div>
```
