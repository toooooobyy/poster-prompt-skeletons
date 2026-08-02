# Cyberpunk Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the cyberpunk neon-noir poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **cyberpunk neon-noir poster designer** working within the futuristic dystopian aesthetic framework. Your core language is blue-purple cold-tone neon light, rainy-night hazy glow, and glitch-art texture. You produce 9:16 vertical brand calendar posters that feel futuristic, moody, and electric, rejecting any warm pastoral tone or flat sterile minimalism.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, neon-edged dark grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ glow    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (cyberpunk city)           │
│                             │
├─────────┤──────────────────┤
│ TITLE   │                  │
│ Subtitle│   [QR CODE]      │  ← BOTTOM ZONE
│ ─────── │                  │
│ Contact │                  │
└─────────┴──────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Square LOGO (dark bg + neon outline) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical neon hairline |
| Main visual | Top-right, large area | Replaceable cyberpunk city illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal neon hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Neon divider | Full width | One horizontal glowing hairline |

**Layout prohibitions:** No warm pastel palettes, no pastoral natural scenery, no sterile flat white backgrounds. Keep the dark neon-noir atmosphere throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Cyberpunk neon-noir, blue-purple cold tone, rainy-night hazy light, glitch texture |
| Base color | Deep dark blue `#0A0E27` |
| Texture | Glitch art bands, scanlines, neon bloom, rain streaks, digital noise |
| Main visual type | Cyberpunk city illustration (NOT pastoral photography, NOT flat vector, NOT watercolor) |
| Date font | Oversized bold serif with neon glow + subtle glitch |
| Weekday font | All-caps monospace/tech sans, wide tracking |
| Title font | Bold serif Chinese with faint neon edge glow |
| Auxiliary text | Thin tech sans-serif, cool light tone |
| Light | Neon bloom, wet reflective streets, hazy fog |

---

## 4. Seasonal Color System

| Season | Months | Base | Neon accent |
|--------|--------|------|-------------|
| Spring | Mar–May | Deep blue base `#0A0E27` | Emerald green neon |
| Summer | Jun–Aug | Deep blue base `#0A0E27` | Magenta neon |
| Autumn | Sep–Nov | Deep blue base `#0A0E27` | Amber neon |
| Winter | Dec–Feb | Deep blue base `#0A0E27` | Ice-blue neon |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** futuristic, electric, moody; may carry a sense of neon-lit solitude

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 霓虹纪元  (4–8 chars)
{SUBTITLE}         e.g., 在雨夜的霓虹里，看见未来的脉搏  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., cyberpunk megacity skyline with magenta neon reflections on wet streets
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #0A0E27
{NEON_COLOR}       e.g., magenta neon
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match cyberpunk city scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#0A0E27` |
| {NEON_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — cyberpunk neon-noir style, blue-purple cold tone

A 9:16 vertical poster in cyberpunk neon-noir style. Blue-purple cold tone, rainy-night hazy neon glow, glitch-art bands, scanlines, and digital noise texture. Six fixed zones with a glowing neon divider hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, neon accent color {NEON_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block (dark background with a thin {NEON_COLOR} neon outline) next to the English company name "{COMPANY_EN}" in thin uppercase tech sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps tech sans-serif with wide tracking, an oversized bold serif numeral "{DATE_NUMBER}" with neon glow and subtle glitch, and the month "{MONTH}" below. A vertical neon hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Cyberpunk city illustration: neon bloom, wet reflective streets, hazy fog, deep blue dark base. No pastoral scenery, no flat vector, no watercolor.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese with faint neon edge glow, subtitle "{SUBTITLE}" in thin tech sans-serif below, followed by a horizontal neon hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small tech sans-serif.
- FULL WIDTH BOTTOM: A single horizontal glowing neon hairline.

MOOD: Futuristic, electric, moody, neon-lit solitude. No warm pastoral tone, no sterile flat minimalism.

STYLE REFERENCES: Cyberpunk 2077 aesthetic, Blade Runner neon-noir, retrowave cityscapes, glitch-art posters.

NEGATIVE: No warm pastel palettes, no pastoral natural scenery, no sterile flat white background, no photography, no watercolor, no ink wash, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No warm pastel, no pastoral scenery, no sterile white |
| 3 | Illustration style | Cyberpunk city with neon bloom, glitch, rain haze |
| 4 | Painting style | No pastoral / watercolor / flat vector tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Deep blue base with neon accent glow present; not overly bright or warm |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in cyberpunk style.
```

**Full variable call:**
```
Generate in cyberpunk style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 霓虹纪元
SUBTITLE: 在雨夜的霓虹里，看见未来的脉搏
MAIN_VISUAL_DESC: cyberpunk megacity skyline with magenta neon reflections on wet streets
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #0A0E27
NEON_COLOR: magenta neon
```
