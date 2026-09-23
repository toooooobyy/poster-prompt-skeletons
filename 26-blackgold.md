# Black-Gold Luxury Business Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the black-gold luxury minimalist business poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **black-gold luxury business poster designer** working within a refined executive aesthetic framework. Your core language is a deep blue/grey matte ground, fine gold-line accents, and restrained whitespace. You produce 9:16 vertical brand calendar posters that feel premium, calm, and authoritative, rejecting any gaudy clutter or casual playfulness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, restrained executive grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ gold    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (black-gold graphic)       │
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
| LOGO column | Top-left | Square LOGO (gold-line frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical fine gold hairline |
| Main visual | Top-right, large area | Replaceable black-gold minimalist graphic zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal gold hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Gold divider | Full width | One horizontal fine gold hairline |

**Layout prohibitions:** No gaudy clutter, no casual playfulness, no neon, no dense patterns. Keep the restrained premium whitespace throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Black-gold luxury, deep blue/grey matte ground, fine gold-line accents, restrained whitespace |
| Base color | Deep blue-black `#0F1923` |
| Texture | Matte, fine grain, subtle metal sheen on gold |
| Main visual type | Black-gold minimalist graphic (NOT photography, NOT neon, NOT dense pattern) |
| Date font | Oversized light serif, gold tone |
| Weekday font | All-caps thin sans-serif, wide tracking, light gold |
| Title font | Bold serif Chinese, gold-ink |
| Auxiliary text | Thin sans-serif, light gold-grey |

---

## 4. Seasonal Color System

| Season | Months | Base | Gold | Accent |
|--------|--------|------|------|--------|
| Spring | Mar–May | Deep blue base | Gold | Green |
| Summer | Jun–Aug | Deep blue base | Gold | Blue |
| Autumn | Sep–Nov | Deep blue base | Gold | Brown |
| Winter | Dec–Feb | Deep grey base | Gold | Silver |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** premium, calm, authoritative; may carry a sense of quiet confidence

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 沉稳之境  (4–8 chars)
{SUBTITLE}         e.g., 于克制的留白间，彰显非凡的气度  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., black-gold minimalist graphic of fine geometric lines forming an abstract monogram
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #0F1923
{GOLD_COLOR}       e.g., gold
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match black-gold graphic by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#0F1923` |
| {GOLD_COLOR} | Gold |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — black gold luxury business style

A 9:16 vertical poster in black-gold luxury minimalist business style. Deep blue/dark gray matte base, fine gold line accents, restrained whitespace, premium feel. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, gold {GOLD_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small fine-line gold LOGO beside the English company name "{COMPANY_EN}" in ultra-thin all-caps sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in thin serif with gold accent, right-aligned.
- CENTER (offset, restrained): The main visual — a black gold minimalist graphic: {MAIN_VISUAL_DESC}. Dark matte background ({BASE_COLOR}), fine gold line elements ({GOLD_COLOR}), minimal composition, large negative space. Premium, understated, luxurious.
- MID-LOWER: Main title "{MAIN_TITLE}" in ultra-thin sans-serif Chinese with gold accent line, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Deep dark blue-gray ({BASE_COLOR}) matte finish with subtle fine gold line accents ({GOLD_COLOR}) and minimal decoration.

MOOD: Premium, luxurious, restrained, sophisticated. No promotional tone.

STYLE REFERENCES: Luxury brand minimalism, black-gold premium design, fine-line gold detailing, dark matte finishes, high-end business aesthetics.

NEGATIVE: No bright colors, no photography, no 3D render, no illustration, no high saturation, no decorative patterns, no gradients, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No gaudy clutter, no neon, no dense pattern |
| 3 | Illustration style | Black-gold minimalist with fine gold lines |
| 4 | Painting style | No neon / photography / dense tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Deep matte ground with restrained gold; not overly bright |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in black-gold business style.
```

**Full variable call:**
```
Generate in black-gold business style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 沉稳之境
SUBTITLE: 于克制的留白间，彰显非凡的气度
MAIN_VISUAL_DESC: black-gold minimalist graphic of fine geometric lines forming an abstract monogram
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #0F1923
GOLD_COLOR: gold
```
