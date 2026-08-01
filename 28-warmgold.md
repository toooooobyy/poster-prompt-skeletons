# Warm Gold Business Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the warm-gold cozy business poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **warm-gold business poster designer** working within a cozy premium aesthetic framework. Your core language is a beige-gold light-brown soft ground, fine scattered micro-light gold-foil texture, and soft diffused lighting. You produce 9:16 vertical brand calendar posters that feel warm, inviting, and quietly premium, rejecting any cold sterility or gaudy shine.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, warm premium grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ gold    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (warm gold graphic)        │
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
| LOGO column | Top-left | Square LOGO (soft gold frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical fine gold hairline |
| Main visual | Top-right, large area | Replaceable warm-gold business graphic zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal gold hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Gold divider | Full width | One horizontal fine gold hairline |

**Layout prohibitions:** No cold sterility, no gaudy shine, no neon, no harsh contrast. Keep the warm inviting premium softness throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Warm-gold business, beige-gold light-brown soft ground, fine scattered gold-foil micro-light, soft diffused light |
| Base color | Beige-gold `#F0E6D6` |
| Texture | Fine scattered gold-foil micro-light, soft diffused, matte-warm |
| Main visual type | Warm-gold business graphic (NOT photography, NOT neon, NOT harsh 3D) |
| Date font | Oversized soft serif, warm gold |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, warm gold-ink |
| Auxiliary text | Thin sans-serif, muted warm gold |

---

## 4. Seasonal Color System

| Season | Months | Base | Gold accent |
|--------|--------|------|-------------|
| Spring | Mar–May | Beige-gold base | Tender green |
| Summer | Jun–Aug | Beige-gold base | Light blue |
| Autumn | Sep–Nov | Beige-gold base | Caramel |
| Winter | Dec–Feb | Beige-gold base | Silver grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** warm, inviting, quietly premium; may carry a sense of gentle hospitality

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 温润之礼  (4–8 chars)
{SUBTITLE}         e.g., 于微光金箔间，传递一份温润的心意  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., warm-gold business graphic of soft abstract ribbons with scattered gold-foil micro-light
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
{BASE_COLOR}       e.g., #F0E6D6
{GOLD_COLOR}       e.g., gold
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match warm-gold graphic by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#F0E6D6` |
| {GOLD_COLOR} | Gold |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — warm-gold cozy business style with gold-foil micro-light

A 9:16 vertical poster in warm-gold cozy business style. Beige-gold light-brown soft ground, fine scattered gold-foil micro-light texture, soft diffused lighting, matte-warm. Six fixed zones with a fine gold divider hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, gold color {GOLD_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a soft gold frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized soft serif numeral "{DATE_NUMBER}" (warm gold, visually dominant), and the month "{MONTH}" below. A vertical fine gold hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Warm-gold business graphic: soft abstract forms, scattered gold-foil micro-light, diffused light. No photography, no neon, no harsh 3D.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (warm gold-ink), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal gold hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal fine gold hairline.

MOOD: Warm, inviting, quietly premium, gentle hospitality. No cold sterility, no gaudy shine.

STYLE REFERENCES: Warm premium hospitality branding, gold-foil micro-light textures, soft diffused beige-gold palettes, matte-warm business design.

NEGATIVE: No cold sterility, no gaudy shine, no neon, no harsh contrast, no photography, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No cold sterility, no gaudy shine, no neon |
| 3 | Illustration style | Warm-gold with scattered gold-foil micro-light |
| 4 | Painting style | No neon / photography / harsh 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Warm beige-gold palette present; not overly cold or garish |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in warm-gold business style.
```

**Full variable call:**
```
Generate in warm-gold business style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 温润之礼
SUBTITLE: 于微光金箔间，传递一份温润的心意
MAIN_VISUAL_DESC: warm-gold business graphic of soft abstract ribbons with scattered gold-foil micro-light
SEASON: Summer
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #F0E6D6
GOLD_COLOR: gold
```
