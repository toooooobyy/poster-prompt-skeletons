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
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
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

A 9:16 vertical poster in premium-gray minimalist business style. All-tone low-saturation gray base, minimal geometric thin-line divisions, large whitespace. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small minimal LOGO beside the English company name "{COMPANY_EN}" in ultra-thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in light sans-serif, right-aligned.
- CENTER (offset, minimal): The main visual — a premium gray minimalist flat graphic: {MAIN_VISUAL_DESC}. Low-saturation gray palette, minimal geometric thin-line elements, large negative space (~50% whitespace). Colors limited to {BASE_COLOR} and {ACCENT_COLOR}. Sophisticated, understated, refined.
- MID-LOWER: Main title "{MAIN_TITLE}" in ultra-thin sans-serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Thin geometric divider. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Premium low-saturation gray ({BASE_COLOR}) with minimal geometric thin-line divisions and large whitespace.

MOOD: Sophisticated, understated, refined, premium. No promotional tone.

STYLE REFERENCES: Premium gray minimalist design, high-end business aesthetics, Swiss whitespace design, low-saturation gray palettes, refined corporate layout.

NEGATIVE: No high saturation, no warm tones, no photography, no 3D render, no illustration, no decorative ornaments, no gradients, no promotional banners, no emoji, no icons in contact area.
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
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #D0D0D0
ACCENT_COLOR: grey-blue
```
