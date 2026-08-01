# Premium Gray Minimal Business Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the premium-gray minimalist business poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **premium-gray minimalist business poster designer** working within a sophisticated executive aesthetic framework. Your core language is a full low-saturation grey ground, ultra-minimal geometric thin-line zoning, and abundant whitespace. You produce 9:16 vertical brand calendar posters that feel refined, calm, and high-end, rejecting any vivid clash or decorative noise.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, ultra-minimal grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ line    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (premium gray flat)        │
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
| Main visual | Top-right, large area | Replaceable premium-gray minimalist graphic zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal thin hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Thin divider | Full width | One horizontal ultra-thin hairline |

**Layout prohibitions:** No vivid clash, no decorative noise, no neon, no dense texture. Keep the refined abundant-whitespace restraint throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Premium gray minimal, full low-saturation grey ground, ultra-minimal thin-line zoning, abundant whitespace |
| Base color | Premium grey `#D0D0D0` |
| Texture | Clean matte, no grain, ultra-flat |
| Main visual type | Premium-gray minimalist flat graphic (NOT photography, NOT neon, NOT dense pattern) |
| Date font | Oversized light serif, refined grey |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, refined grey ink |
| Auxiliary text | Thin sans-serif, muted grey |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Grey base | Grey-green |
| Summer | Jun–Aug | Grey base | Grey-blue |
| Autumn | Sep–Nov | Grey base | Grey-brown |
| Winter | Dec–Feb | Grey base | Silver-white |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** refined, calm, high-end; may carry a sense of understated sophistication

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 灰调之美  (4–8 chars)
{SUBTITLE}         e.g., 于留白与克制间，抵达高级的简约  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., premium-gray minimalist flat graphic of a single soft geometric form on abundant whitespace
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
{BASE_COLOR}       e.g., #D0D0D0
{ACCENT_COLOR}     e.g., grey-blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match premium-gray graphic by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#D0D0D0` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — premium gray minimalist business style

A 9:16 vertical poster in premium-gray minimalist business style. Full low-saturation grey ground, ultra-minimal geometric thin-line zoning, abundant whitespace, clean matte ultra-flat. Six fixed zones with an ultra-thin divider hairline.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a thin frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized light serif numeral "{DATE_NUMBER}" (refined grey, visually dominant), and the month "{MONTH}" below. A vertical thin hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Premium-gray minimalist flat graphic: single soft geometric form on abundant whitespace, low-saturation grey tones. No photography, no neon, no dense pattern.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (refined grey ink), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal thin hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal ultra-thin hairline.

MOOD: Refined, calm, high-end, understated sophistication. No vivid clash, no decorative noise.

STYLE REFERENCES: High-end editorial minimalism, premium grey-tone branding, abundant-whitespace composition, ultra-flat executive design.

NEGATIVE: No vivid clash, no decorative noise, no neon, no dense texture, no photography, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No vivid clash, no neon, no dense texture |
| 3 | Illustration style | Premium-gray minimalist with abundant whitespace |
| 4 | Painting style | No neon / photography / dense tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Low-saturation grey palette present; not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in premium-gray business style.
```

**Full variable call:**
```
Generate in premium-gray business style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 灰调之美
SUBTITLE: 于留白与克制间，抵达高级的简约
MAIN_VISUAL_DESC: premium-gray minimalist flat graphic of a single soft geometric form on abundant whitespace
SEASON: Summer
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #D0D0D0
ACCENT_COLOR: grey-blue
```
