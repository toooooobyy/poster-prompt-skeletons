# Memphis Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Memphis high-saturation clash-geometry poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Memphis-style poster designer** working within the playful 1980s Memphis Group aesthetic framework. Your core language is high-saturation clashing geometry, dots, waves, zigzags, and free playful composition. You produce 9:16 vertical brand calendar posters that feel energetic, fun, and bold, rejecting any muted restraint or rigid corporate flatness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, playful geometric grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ dots    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (Memphis collage)          │
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
| LOGO column | Top-left | Square LOGO (bold frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical zigzag divider |
| Main visual | Top-right, large area | Replaceable Memphis geometric collage zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal wavy hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Playful divider | Full width | One horizontal zigzag/wavy line |

**Layout prohibitions:** No muted low-saturation palettes, no rigid corporate grids, no photorealistic detail. Keep the high-saturation playful energy throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Memphis, high-saturation clash geometry, dots/waves/zigzags, free playful composition |
| Base color | Pure white `#FFFFFF` |
| Texture | Flat vector, bold flat shapes, no soft gradients |
| Main visual type | Memphis geometric collage (NOT photography, NOT soft watercolor, NOT 3D) |
| Date font | Oversized bold rounded sans-serif, playful |
| Weekday font | All-caps bold sans-serif, wide tracking |
| Title font | Bold rounded sans-serif Chinese, energetic |
| Auxiliary text | Bold sans-serif |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent | Pattern color |
|--------|--------|------|--------|---------------|
| Spring | Mar–May | White base | Pink | Green / yellow |
| Summer | Jun–Aug | White base | Blue | Orange / yellow |
| Autumn | Sep–Nov | White base | Red | Brown / yellow |
| Winter | Dec–Feb | White base | Blue | Purple / grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** energetic, playful, bold; may carry a sense of fun optimism

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 趣味无界  (4–8 chars)
{SUBTITLE}         e.g., 用撞色与几何，拼出夏日的快乐  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., Memphis collage of bold triangles, dots, squiggles and zigzags in blue orange yellow
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #FFFFFF
{ACCENT_COLOR}     e.g., blue
{PATTERN_COLOR}    e.g., orange / yellow
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match Memphis collage by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#FFFFFF` |
| {ACCENT_COLOR} | Match {SEASON} palette |
| {PATTERN_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Memphis high-saturation clash-geometry style

A 9:16 vertical poster in playful Memphis style. High-saturation clashing geometry, dots, waves, zigzags, free playful composition, bold flat vector shapes. Six fixed zones with a playful zigzag/wavy divider.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}, pattern color {PATTERN_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a bold frame next to the English company name "{COMPANY_EN}" in bold uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps bold sans-serif with wide tracking, an oversized bold rounded sans-serif numeral "{DATE_NUMBER}" (playful, visually dominant), and the month "{MONTH}" below. A vertical zigzag divider runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Memphis geometric collage: bold triangles, dots, squiggles, zigzags, high-saturation clash. Flat vector, no soft gradients, no photography, no watercolor.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold rounded sans-serif Chinese (energetic), subtitle "{SUBTITLE}" in bold sans-serif below, followed by a horizontal wavy hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal zigzag/wavy line.

MOOD: Energetic, playful, bold, fun optimism. No muted restraint, no rigid corporate flatness.

STYLE REFERENCES: Memphis Group (1980s) design, Ettore Sottsass, bold clashing postmodern geometry, playful flat collage.

NEGATIVE: No muted low-saturation palettes, no rigid corporate grids, no photorealistic detail, no soft watercolor, no 3D, no soft gradients, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No muted palette, no soft gradient, no photorealism |
| 3 | Illustration style | Memphis bold geometric collage with dots/waves/zigzags |
| 4 | Painting style | No watercolor / corporate flat / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | High-saturation clash present; not overly muted |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Memphis style.
```

**Full variable call:**
```
Generate in Memphis style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 趣味无界
SUBTITLE: 用撞色与几何，拼出夏日的快乐
MAIN_VISUAL_DESC: Memphis collage of bold triangles, dots, squiggles and zigzags in blue orange yellow
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #FFFFFF
ACCENT_COLOR: blue
PATTERN_COLOR: orange / yellow
```
