# Hand-drawn Flat Texture Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the hand-drawn flat texture poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **hand-drawn flat-texture poster designer** working within a warm illustrative aesthetic framework. Your core language is soft hand-drawn brush strokes, paper-noise grain texture, and low-saturation flat color blocks. You produce 9:16 vertical brand calendar posters that feel warm, handmade, and approachable, rejecting any cold sterile vector or photorealistic hardness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, warm hand-drawn grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ stroke  │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (hand-drawn flat art)      │
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
| LOGO column | Top-left | Square LOGO (hand-drawn frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical hand-drawn stroke |
| Main visual | Top-right, large area | Replaceable hand-drawn flat illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal hand-drawn hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Hand-drawn divider | Full width | One horizontal soft stroke line |

**Layout prohibitions:** No cold sterile vector, no photorealistic hardness, no neon. Keep the warm handmade paper-grain softness throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Hand-drawn flat, soft brush strokes, paper-noise grain, low-saturation color blocks |
| Base color | Warm white `#F5F0E8` |
| Texture | Paper noise grain, soft brush, handmade warmth |
| Main visual type | Hand-drawn flat illustration (NOT cold vector, NOT photography, NOT neon) |
| Date font | Oversized soft serif, hand-drawn warmth |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, soft warm ink |
| Auxiliary text | Thin sans-serif, muted warm |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Warm white | Tender green |
| Summer | Jun–Aug | Warm white | Light blue |
| Autumn | Sep–Nov | Warm white | Ochre-orange |
| Winter | Dec–Feb | Warm white | Grey-blue |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** warm, handmade, approachable; may carry a sense of gentle craft

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 手作温度  (4–8 chars)
{SUBTITLE}         e.g., 在笔触与肌理间，感受手作的温柔  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., hand-drawn flat illustration of a cozy desk plant with soft brush strokes and light-blue color blocks
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
{BASE_COLOR}       e.g., #F5F0E8
{ACCENT_COLOR}     e.g., light blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match hand-drawn illustration by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#F5F0E8` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — hand-drawn flat texture style, soft brush and paper grain

A 9:16 vertical poster in warm hand-drawn flat style. Soft hand-drawn brush strokes, paper-noise grain texture, low-saturation flat color blocks, handmade warmth. Six fixed zones with a soft hand-drawn divider stroke.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a hand-drawn frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized soft serif numeral "{DATE_NUMBER}" (hand-drawn warmth, visually dominant), and the month "{MONTH}" below. A vertical hand-drawn stroke runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Hand-drawn flat illustration: soft brush strokes, paper-noise grain, low-saturation color blocks. No cold vector, no photography, no neon.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (soft warm ink), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal hand-drawn hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal soft hand-drawn stroke line.

MOOD: Warm, handmade, approachable, gentle craft. No cold sterile vector, no photorealistic hardness.

STYLE REFERENCES: Contemporary hand-drawn illustration, paper-grain texture art, warm flat editorial illustration, low-saturation craft palettes.

NEGATIVE: No cold sterile vector, no photorealistic hardness, no neon, no photography, no 3D, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No cold vector, no photorealism, no neon |
| 3 | Illustration style | Hand-drawn flat with soft brush and paper grain |
| 4 | Painting style | No cold vector / neon / photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Low-saturation warm palette present; not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in hand-drawn style.
```

**Full variable call:**
```
Generate in hand-drawn style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 手作温度
SUBTITLE: 在笔触与肌理间，感受手作的温柔
MAIN_VISUAL_DESC: hand-drawn flat illustration of a cozy desk plant with soft brush strokes and light-blue color blocks
SEASON: Summer
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #F5F0E8
ACCENT_COLOR: light blue
```
