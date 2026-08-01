# Pop Art Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Pop Art silkscreen poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Pop Art poster designer** working within the Andy Warhol / Roy Lichtenstein silkscreen aesthetic framework. Your core language is thick black outlines, high-contrast clashing colors, and halftone silkscreen dot texture. You produce 9:16 vertical brand calendar posters that feel bold, graphic, and punchy, rejecting any soft muted restraint or photorealistic softness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, bold graphic grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ dots    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (Pop Art illustration)     │
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
| LOGO column | Top-left | Square LOGO (bold black frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical bold black line |
| Main visual | Top-right, large area | Replaceable Pop Art illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal bold black hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Bold divider | Full width | One horizontal thick black line |

**Layout prohibitions:** No soft muted palettes, no photorealistic gradients, no delicate watercolor. Keep the bold graphic punch throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Pop Art, thick black outlines, high-contrast clash, silkscreen halftone dots |
| Base color | Pop yellow `#FFD23F` |
| Texture | Halftone silkscreen dots, flat ink, no soft gradients |
| Main visual type | Pop Art illustration (NOT photography, NOT watercolor, NOT soft 3D) |
| Date font | Oversized bold display sans-serif, punchy |
| Weekday font | All-caps bold sans-serif, wide tracking |
| Title font | Bold display sans-serif Chinese, graphic |
| Auxiliary text | Bold sans-serif |
| Outline | Thick black contour lines throughout |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent | Outline |
|--------|--------|------|--------|---------|
| Spring | Mar–May | Yellow base | Pink | Green |
| Summer | Jun–Aug | Yellow base | Blue | Red |
| Autumn | Sep–Nov | Yellow base | Orange | Brown |
| Winter | Dec–Feb | White base | Blue | Purple |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** bold, graphic, punchy; may carry a sense of playful impact

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 色彩宣言  (4–8 chars)
{SUBTITLE}         e.g., 用撞色与粗线，宣告夏日的张扬  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., Pop Art illustration of bold fruit with thick black outlines and blue red silkscreen dots
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
{BASE_COLOR}       e.g., #FFD23F
{ACCENT_COLOR}     e.g., blue
{OUTLINE_COLOR}    e.g., red
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match Pop Art illustration by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#FFD23F` |
| {ACCENT_COLOR} | Match {SEASON} palette |
| {OUTLINE_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Pop Art silkscreen style, thick outlines and high-contrast clash

A 9:16 vertical poster in bold Pop Art style. Thick black outlines, high-contrast clashing colors, halftone silkscreen dot texture, flat ink with no soft gradients. Six fixed zones with a thick black divider.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}, outline color {OUTLINE_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a bold black frame next to the English company name "{COMPANY_EN}" in bold uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps bold sans-serif with wide tracking, an oversized bold display sans-serif numeral "{DATE_NUMBER}" (punchy, visually dominant), and the month "{MONTH}" below. A vertical bold black line runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Pop Art illustration with thick black outlines and high-contrast clashing colors, silkscreen halftone dots. No photography, no watercolor, no soft 3D.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold display sans-serif Chinese (graphic), subtitle "{SUBTITLE}" in bold sans-serif below, followed by a horizontal thick black hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal thick black line.

MOOD: Bold, graphic, punchy, playful impact. No soft muted restraint, no photorealistic softness.

STYLE REFERENCES: Andy Warhol silkscreen, Roy Lichtenstein halftone comics, bold graphic Pop Art posters.

NEGATIVE: No soft muted palettes, no photorealistic gradients, no delicate watercolor, no soft 3D, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No soft gradient, no watercolor, no photorealism |
| 3 | Illustration style | Pop Art with thick outlines and halftone dots |
| 4 | Painting style | No watercolor / muted / soft 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | High-contrast clash present; not overly muted |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Pop Art style.
```

**Full variable call:**
```
Generate in Pop Art style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 色彩宣言
SUBTITLE: 用撞色与粗线，宣告夏日的张扬
MAIN_VISUAL_DESC: Pop Art illustration of bold fruit with thick black outlines and blue red silkscreen dots
SEASON: Summer
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #FFD23F
ACCENT_COLOR: blue
OUTLINE_COLOR: red
```
