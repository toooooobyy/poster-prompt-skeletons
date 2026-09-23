# Natural Forest Minimal Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the natural forest soft-green poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **natural forest-style poster designer** working within the fresh botanical aesthetic framework. Your core language is a softly blurred green-plant background, low-saturation plant-and-earth tones, and clean natural simplicity. You produce 9:16 vertical brand calendar posters that feel fresh, calm, and organic, rejecting any harsh industrial edge or artificial neon tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, soft botanical grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ stem    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (natural greenery)         │
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
| LOGO column | Top-left | Square LOGO (soft frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical thin stem line |
| Main visual | Top-right, large area | Replaceable natural greenery photography zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Soft divider | Full width | One horizontal thin hairline |

**Layout prohibitions:** No harsh industrial elements, no neon, no artificial heavy contrast. Keep the fresh organic softness throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Natural forest, soft blurred greenery background, low-saturation plant tones, fresh clean |
| Base color | Light plant white `#F0F2EC` |
| Texture | Soft bokeh blur, natural light, gentle depth of field |
| Main visual type | Natural greenery photography (NOT neon vector, NOT heavy oil paint, NOT 3D render) |
| Date font | Oversized soft serif, natural tone |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, soft natural ink |
| Auxiliary text | Thin sans-serif, muted green-grey |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Light plant white | Tender green |
| Summer | Jun–Aug | Light plant white | Deep green |
| Autumn | Sep–Nov | Light plant white | Withered yellow |
| Winter | Dec–Feb | Light plant white | Silver grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** fresh, calm, organic; may carry a sense of natural stillness

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 林间清欢  (4–8 chars)
{SUBTITLE}         e.g., 在绿意深处，听见季节的低语  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., softly blurred deep-green ferns and leaves with morning light bokeh
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #F0F2EC
{ACCENT_COLOR}     e.g., deep green
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match natural greenery by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#F0F2EC` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — forest natural minimalist style

A 9:16 vertical poster in forest-natural minimalist style. Blurred soft-focus greenery background, low-saturation plant-tone palette, fresh and natural atmosphere. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small leaf-outline LOGO beside the English company name "{COMPANY_EN}" in thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in light serif.
- CENTER (large area): The main visual — nature plant photography: {MAIN_VISUAL_DESC}. Soft-focus blurred greenery background, gentle natural light, low saturation, fresh atmosphere. Accent color ({ACCENT_COLOR}) in subtle plant details. Shallow depth of field.
- MID-LOWER: Main title "{MAIN_TITLE}" in light serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Soft pale green-gray ({BASE_COLOR}) with faint blurred plant shadows and natural light diffusion.

MOOD: Fresh, natural, calm, healing. No promotional tone.

STYLE REFERENCES: Nature photography, botanical minimalist design, soft-focus bokeh, Muji natural aesthetic, slow-living lifestyle.

NEGATIVE: No high saturation, no strong contrast, no urban scenes, no illustration, no 3D render, no sharp focus, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No neon, no industrial edge, no heavy contrast |
| 3 | Illustration style | Natural greenery with soft bokeh blur |
| 4 | Painting style | No oil paint / 3D / neon vector tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Low-saturation plant palette present; not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in forest style.
```

**Full variable call:**
```
Generate in forest style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 林间清欢
SUBTITLE: 在绿意深处，听见季节的低语
MAIN_VISUAL_DESC: softly blurred deep-green ferns and leaves with morning light bokeh
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #F0F2EC
ACCENT_COLOR: deep green
```
