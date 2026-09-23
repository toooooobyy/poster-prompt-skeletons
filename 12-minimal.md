# Minimalist Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the minimalist large-whitespace poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **minimalist poster designer** working within the clean, flat, generous-whitespace aesthetic framework. Your core language is large empty space, a single dominant visual, soft clean base color, and flat texture. You produce 9:16 vertical brand calendar posters that feel calm, pure, and uncluttered, rejecting any ornate decoration or dense visual noise.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, airy generous grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ line    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (single flat block)        │
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
| LOGO column | Top-left | Square LOGO (thin frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical thin hairline |
| Main visual | Top-right, large area | Replaceable single flat color-block zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Bottom hairline | Full width | One horizontal 1px line |

**Layout prohibitions:** No ornate decoration, no dense patterns, no heavy shadows, no texture noise. Keep the clean airy whitespace throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Minimalist, large whitespace, single dominant visual, flat clean texture |
| Base color | Soft white `#FAFAF8` |
| Texture | Flat, clean, no grain, no noise |
| Main visual type | Minimal flat color block (NOT photography, NOT 3D, NOT dense pattern) |
| Date font | Oversized light serif, airy |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, clean |
| Auxiliary text | Thin sans-serif, low contrast |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Soft white base | Tender green |
| Summer | Jun–Aug | Soft white base | Light blue |
| Autumn | Sep–Nov | Soft white base | Warm brown |
| Winter | Dec–Feb | Soft white base | Cold grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** calm, pure, uncluttered; may carry a sense of quiet clarity

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 至简之境  (4–8 chars)
{SUBTITLE}         e.g., 留白之处，自有天地  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., a single soft circle flat color block in light blue on generous white space
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #FAFAF8
{ACCENT_COLOR}     e.g., light blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match single flat block by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#FAFAF8` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — minimalist style

A 9:16 vertical poster in strict minimalist style. Large-scale whitespace (~45–50% blank), single dominant visual, clean soft base color. Six fixed zones. No decorative borders.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: Company name "{COMPANY_EN}" in ultra-thin sans-serif, left-aligned.
- TOP-RIGHT: Date numeral "{DATE_NUMBER}" in large light sans-serif, right-aligned, with weekday "{WEEKDAY}" and month "{MONTH}" in small caps below.
- CENTER (offset, single element): The main visual — a minimalist flat block composition: {MAIN_VISUAL_DESC}. One single clean visual element, maximum negative space, subtle accent color ({ACCENT_COLOR}) used sparingly. No clutter.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in light-weight sans-serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Clean soft off-white ({BASE_COLOR}) with no texture.

MOOD: Calm, clean, spacious, refined. No promotional tone.

STYLE REFERENCES: Dieter Rams design principles, Apple minimalist aesthetic, Swiss whitespace design, Muji catalog layout.

NEGATIVE: No decoration, no patterns, no gradients, no textures, no multiple visual elements, no borders, no photography, no 3D render, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No heavy shadow, no dense pattern, no grain |
| 3 | Illustration style | Single flat color block with generous whitespace |
| 4 | Painting style | No photography / 3D / ornate tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Soft clean palette with airy whitespace; not overly dense |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in minimalist style.
```

**Full variable call:**
```
Generate in minimalist style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 至简之境
SUBTITLE: 留白之处，自有天地
MAIN_VISUAL_DESC: a single soft circle flat color block in light blue on generous white space
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #FAFAF8
ACCENT_COLOR: light blue
```
