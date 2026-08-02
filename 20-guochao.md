# Guochao Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Guochao (国潮) red-gold poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Guochao poster designer** working within the contemporary Chinese-trend (国潮) aesthetic framework. Your core language is traditional patterns combined with bold geometric color blocks, red-gold color clashing, and flat国风 graphics. You produce 9:16 vertical brand calendar posters that feel bold, festive, and culturally proud, rejecting any muted restraint or western-minimal sterility.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, bold国潮 grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ gold    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (国潮 flat pattern)         │
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
| LOGO column | Top-left | Square LOGO (gold frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical gold hairline |
| Main visual | Top-right, large area | Replaceable国潮 flat-pattern zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal gold hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Gold divider | Full width | One horizontal gold hairline |

**Layout prohibitions:** No muted restraint, no western-minimal sterility, no soft watercolor. Keep the bold red-gold国潮 energy throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Guochao国潮, traditional patterns + bold geometric blocks, red-gold clash, flat国风 graphics |
| Base color | Guochao red `#C8102E` |
| Texture | Flat vector, bold ink, traditional pattern motifs |
| Main visual type | 国潮 flat pattern illustration (NOT photography, NOT soft watercolor, NOT 3D) |
| Date font | Oversized bold serif, festive |
| Weekday font | All-caps bold sans-serif, wide tracking |
| Title font | Bold serif Chinese, gold-ink |
| Auxiliary text | Bold sans-serif, light tone |
| Motif | Traditional patterns (回纹/云纹) as bold flat accents |

---

## 4. Seasonal Color System

| Season | Months | Base | Gold | Pattern color |
|--------|--------|------|------|---------------|
| Spring | Mar–May | Red base | Gold | Pink-green |
| Summer | Jun–Aug | Red base | Gold | Cyan-blue |
| Autumn | Sep–Nov | Red base | Gold | Ochre-yellow |
| Winter | Dec–Feb | Red base | Gold | Ink-black |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** bold, festive, culturally proud; may carry a sense of Eastern vigor

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 国潮新韵  (4–8 chars)
{SUBTITLE}         e.g., 以红金撞色，写就东方的新潮  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., 国潮 flat pattern of bold dragons and clouds in red gold and cyan-blue
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #C8102E
{GOLD_COLOR}       e.g., gold
{PATTERN_COLOR}    e.g., cyan-blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match国潮 pattern by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#C8102E` |
| {GOLD_COLOR} | Gold |
| {PATTERN_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Guochao 国潮 red-gold flat-pattern style

A 9:16 vertical poster in bold Guochao 国潮 style. Traditional patterns combined with bold geometric color blocks, red-gold color clashing, flat 国风 graphics, bold ink. Six fixed zones with a gold divider hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, gold color {GOLD_COLOR}, pattern color {PATTERN_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a gold frame next to the English company name "{COMPANY_EN}" in bold uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps bold sans-serif with wide tracking, an oversized bold serif numeral "{DATE_NUMBER}" (festive, visually dominant), and the month "{MONTH}" below. A vertical gold hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. 国潮 flat pattern: traditional motifs (回纹/云纹) with bold geometric blocks, red-gold clash. No photography, no soft watercolor, no 3D.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (gold-ink), subtitle "{SUBTITLE}" in bold sans-serif below, followed by a horizontal gold hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal gold hairline.

MOOD: Bold, festive, culturally proud, Eastern vigor. No muted restraint, no western-minimal sterility.

STYLE REFERENCES: Contemporary 国潮 graphic design, traditional Chinese patterns reinterpreted flat, red-gold festive palettes, bold Eastern typography.

NEGATIVE: No muted restraint, no western-minimal sterility, no soft watercolor, no photography, no 3D, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No muted palette, no watercolor, no photorealism |
| 3 | Illustration style | 国潮 flat pattern with red-gold clash |
| 4 | Painting style | No watercolor / western-minimal / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Bold red-gold palette present; not overly muted |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in 国潮 style.
```

**Full variable call:**
```
Generate in 国潮 style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 国潮新韵
SUBTITLE: 以红金撞色，写就东方的新潮
MAIN_VISUAL_DESC: 国潮 flat pattern of bold dragons and clouds in red gold and cyan-blue
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #C8102E
GOLD_COLOR: gold
PATTERN_COLOR: cyan-blue
```
