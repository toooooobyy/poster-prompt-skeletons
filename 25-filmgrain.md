# Film Grain Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the film-grain warm-soft-focus poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **film-grain poster designer** working within the analog photographic aesthetic framework. Your core language is film-grain noise texture, warm-tone soft-focus light-shadow, and hazy atmospheric mood. You produce 9:16 vertical brand calendar posters that feel nostalgic, cinematic, and atmospheric, rejecting any crisp digital sterility or harsh neon edge.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, cinematic soft grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ soft    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (film photo mood)          │
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
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical soft hairline |
| Main visual | Top-right, large area | Replaceable film-photography mood zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal soft hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Soft divider | Full width | One horizontal soft hairline |

**Layout prohibitions:** No crisp digital sterility, no harsh neon edge, no flat vector. Keep the warm hazy film-grain atmosphere throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Film grain, warm-tone soft-focus light-shadow, hazy atmospheric mood |
| Base color | Warm light brown `#EDE5DC` |
| Texture | Film-grain noise, soft focus, light leaks, warm fade |
| Main visual type | Film-photography mood (NOT crisp digital, NOT flat vector, NOT neon) |
| Date font | Oversized soft serif, warm faded |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, warm ink |
| Auxiliary text | Thin sans-serif, muted warm |
| Light | Soft-focus, light leaks, warm haze |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Warm light brown | Tender green |
| Summer | Jun–Aug | Warm light brown | Sea blue |
| Autumn | Sep–Nov | Warm light brown | Caramel |
| Winter | Dec–Feb | Warm light brown | Cold grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** nostalgic, cinematic, atmospheric; may carry a sense of warm reverie

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 胶片时光  (4–8 chars)
{SUBTITLE}         e.g., 在颗粒与柔焦里，留住一帧旧时光  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., film-grain photograph of a seaside afternoon with sea-blue tones and soft light leak
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #EDE5DC
{ACCENT_COLOR}     e.g., sea blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match film mood scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#EDE5DC` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — film grain style

A 9:16 vertical poster in film-grain photography style. Film noise grain texture, warm-tone soft-focus light, blurred atmospheric depth. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small minimal LOGO beside the English company name "{COMPANY_EN}" in thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in light serif.
- CENTER (large area): The main visual — film photography texture: {MAIN_VISUAL_DESC}. Warm-tone soft focus, film grain noise, light leaks, shallow depth of field, faded vintage feel. Accent color ({ACCENT_COLOR}) in subtle highlights. Atmospheric, dreamy, nostalgic.
- MID-LOWER: Main title "{MAIN_TITLE}" in light serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Warm cream ({BASE_COLOR}) with film grain noise, subtle light leaks, and soft vignette.

MOOD: Nostalgic, atmospheric, dreamy, warm. No promotional tone.

STYLE REFERENCES: 35mm film photography, faded vintage film tones, light leaks, film grain texture, analog photography aesthetic, Lomography.

NEGATIVE: No digital sharpness, no 3D render, no illustration, no high saturation, no modern clean look, no flat vector design, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No crisp digital, no neon, no flat vector |
| 3 | Illustration style | Film-grain with soft focus and warm light leaks |
| 4 | Painting style | No flat vector / neon / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Warm faded palette present; not overly crisp or vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in film-grain style.
```

**Full variable call:**
```
Generate in film-grain style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 胶片时光
SUBTITLE: 在颗粒与柔焦里，留住一帧旧时光
MAIN_VISUAL_DESC: film-grain photograph of a seaside afternoon with sea-blue tones and soft light leak
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #EDE5DC
ACCENT_COLOR: sea blue
```
