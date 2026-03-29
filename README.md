# Dark Presentation

Claude Code skill for generating premium dark-themed HTML presentations as single files.

McKinsey/consulting-style slide decks with keyboard navigation, touch support, and automatic PDF export.

## Preview

<table>
<tr>
<td><img src="https://github.com/user-attachments/assets/placeholder-title" width="400" alt="Title Slide"></td>
<td><img src="https://github.com/user-attachments/assets/placeholder-content" width="400" alt="Content Slide"></td>
</tr>
</table>

> Replace placeholder images with actual screenshots after first use.

## Features

- **Single HTML file** — no build step, no dependencies, opens in any browser
- **Dark theme** — black background + warm cream text + gold/red/green accents
- **Slide navigation** — keyboard arrows, touch swipe, click zones, progress bar
- **12 components** — badge, card, callout, VS block, stat block, timeline, table, etc.
- **Reveal animations** — staggered fade-in on slide transition
- **Unsplash backgrounds** — hero images with gradient overlays
- **Film grain overlay** — SVG noise texture for premium feel
- **Responsive** — mobile/tablet support + print CSS
- **Auto PDF export** — Playwright captures each slide → Pillow combines into PDF
- **Korean-first typography** — Noto Sans KR, Noto Serif KR, Bebas Neue, Cormorant Garamond

## Install

```bash
# Clone to Claude Code skills directory
git clone https://github.com/YOUR_USERNAME/dark-presentation.git ~/.claude/skills/dark-presentation
```

Or copy manually:

```
~/.claude/skills/dark-presentation/
├── SKILL.md
├── README.md
└── references/
    ├── components.md
    └── navigation.md
```

## Usage

In Claude Code, say any of these:

```
프레젠테이션 만들어줘
발표자료 만들어줘
HTML 슬라이드 덱
컨설팅 스타일 발표
presentation
slide deck
```

The skill will:
1. Ask about the topic, audience, and key message
2. Propose a slide outline (10–16 slides)
3. Generate a single HTML file
4. Convert to PDF automatically

## Output Formats

| Format | Best for |
|--------|----------|
| **Slide deck** (default) | Presentations, lectures, meetings |
| **Scroll report** | Reports, policy docs, strategy docs |

## Design System

### Colors

| Token | Hex | Role |
|-------|-----|------|
| `--black` | `#0a0a0a` | Background |
| `--white` | `#f5f2eb` | Warm cream text |
| `--gold` | `#d4b06a` | Primary accent |
| `--red-soft` | `#ef6050` | Crisis / danger |
| `--green` | `#3cc474` | Success / positive |

### Typography

| Font | Use |
|------|-----|
| Bebas Neue | Labels, numbers, impact text |
| Cormorant Garamond | English display quotes |
| Noto Sans KR | Body text, headings |
| Noto Serif KR | Korean quotes |

### Components

`badge` · `card` · `callout` · `vs-block` · `stat-block` · `list-item` · `timeline-row` · `comp-table` · `corner-mark` · `vertical-text` · `divider`

## PDF Export

Requires Python with `playwright` and `Pillow`:

```bash
pip install playwright Pillow
python -m playwright install chromium
```

The skill runs PDF conversion automatically after HTML generation.

## File Structure

```
SKILL.md                 — Main skill (design system, process, checklist)
references/
  components.md          — 12 component CSS + HTML patterns
  navigation.md          — Slide JS, HTML skeleton, Unsplash image IDs
```

## License

MIT
