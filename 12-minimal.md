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
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
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
[PURPOSE]: Brand calendar poster — minimalist large-whitespace flat style

A 9:16 vertical poster in clean minimalist style. Large generous whitespace, a single dominant flat visual, soft clean base color, absolutely flat texture with no grain and no noise. Six fixed zones with a 1px bottom hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a thin frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized light serif numeral "{DATE_NUMBER}" (airy, visually dominant), and the month "{MONTH}" below. A vertical thin hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. A single flat color block on generous whitespace. No photography, no 3D, no dense pattern, no heavy shadow.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (clean), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal 1px hairline.

MOOD: Calm, pure, uncluttered, quiet clarity. No ornate decoration, no dense visual noise.

STYLE REFERENCES: Dieter Rams minimalism, Swiss whitespace design, flat contemporary poster, muji-style calm.

NEGATIVE: No ornate decoration, no dense patterns, no heavy shadows, no texture grain, no photography, no 3D, no promotional text, no sale banners, no emoji, no icons in contact area.
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
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #FAFAF8
ACCENT_COLOR: light blue
```
