# Morandi Texture Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Morandi low-saturation soft-tone poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Morandi-style poster designer** working within the low-saturation grey-tone aesthetic framework of Giorgio Morandi. Your core language is muted soft color blocks, hazy gentle gradations, and matte paper texture. You produce 9:16 vertical brand calendar posters that feel quiet, restrained, and poetic, rejecting any high-saturation clash or hard commercial edge.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, soft muted grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ rule    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (Morandi color blocks)     │
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
| LOGO column | Top-left | Square LOGO (muted frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical soft hairline |
| Main visual | Top-right, large area | Replaceable Morandi abstract color-block zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal soft hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Soft divider | Full width | One horizontal muted hairline |

**Layout prohibitions:** No high-saturation colors, no neon, no hard black contrasts, no glossy reflections. Keep the hazy matte softness throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Morandi low-saturation grey tone, hazy soft color blocks, matte paper texture |
| Base color | Warm muted grey `#D4CFC9` |
| Texture | Matte paper grain, soft dust, gentle blur, no gloss |
| Main visual type | Morandi abstract color-block composition (NOT photography, NOT neon, NOT hard-edge vector) |
| Date font | Oversized soft serif, muted tone |
| Weekday font | All-caps thin sans-serif, wide tracking, low contrast |
| Title font | Bold serif Chinese, softened grey ink |
| Auxiliary text | Thin sans-serif, muted |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Grey-pink base | Grey-green |
| Summer | Jun–Aug | Grey-blue base | Grey-purple |
| Autumn | Sep–Nov | Grey-brown base | Grey-orange |
| Winter | Dec–Feb | Grey-white base | Grey-blue |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** quiet, restrained, poetic; may carry a sense of gentle stillness

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 静默之诗  (4–8 chars)
{SUBTITLE}         e.g., 在低饱和的灰调里，聆听色彩的呼吸  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., Morandi still-life of muted bottles and soft geometric blocks in grey-blue and grey-purple
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #D4CFC9
{ACCENT_COLOR}     e.g., grey-purple
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match Morandi color blocks by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#D4CFC9` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Morandi low-saturation texture style

A 9:16 vertical poster in Morandi low-saturation grey-tone style. Hazy soft color blocks, matte paper grain texture, gentle blur, no gloss, no neon, no hard black contrast. Six fixed zones with a soft muted divider hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a muted frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized soft serif numeral "{DATE_NUMBER}" (muted tone, visually dominant), and the month "{MONTH}" below. A vertical soft hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Morandi abstract color-block composition: low-saturation grey tones, hazy gentle gradations, matte paper texture. No high saturation, no neon, no hard-edge vector, no photography.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (softened grey ink), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal soft hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal muted hairline.

MOOD: Quiet, restrained, poetic, gentle stillness. No high-saturation clash, no hard commercial edge.

STYLE REFERENCES: Giorgio Morandi still-life palette, muted grey-tone interiors, soft matte paper art, low-saturation contemporary illustration.

NEGATIVE: No high-saturation colors, no neon, no hard black contrast, no glossy reflections, no photography, no hard-edge vector, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No high saturation, no neon, no hard black, no gloss |
| 3 | Illustration style | Morandi soft color blocks with matte paper texture |
| 4 | Painting style | No neon / hard-edge / photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Low-saturation grey palette present; not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Morandi style.
```

**Full variable call:**
```
Generate in Morandi style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 静默之诗
SUBTITLE: 在低饱和的灰调里，聆听色彩的呼吸
MAIN_VISUAL_DESC: Morandi still-life of muted bottles and soft geometric blocks in grey-blue and grey-purple
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #D4CFC9
ACCENT_COLOR: grey-purple
```
