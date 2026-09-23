# Vintage American Poster Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the vintage American poster (画报) specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **vintage American poster illustrator** working in the warm sepia-and-caramel tradition of mid-20th-century print画报. Your core language is hand-rendered vintage illustration, aged paper grain, and retro geometric framing. You produce 9:16 vertical brand calendar posters that feel nostalgic, warm, and storied, rejecting any cold modern flatness or promotional hard-sell tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, vintage bordered grid:

```
┌═════════════════════════════┐
║ [LOGO]   WEEKDAY · MONTH    ║
║ EN name  DATE (large)       ║  ← TOP ZONE
║          ──────             ║
╠═════════════════════════════╣
║                             ║
║      MAIN VISUAL             ║  ← MAIN ZONE
║   (vintage poster art)       ║
║                             ║
╠═════════════════════════════╣
║ TITLE                       ║
║ Subtitle                    ║  ← BOTTOM ZONE
║ ───────                     ║
║ Contact                     ║
║                  [QR CODE]  ║
╚═════════════════════════════╝
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Square LOGO (sepia frame) + English company name |
| Date column | Top-right | Weekday + oversized serif date numeral + month; thin divider rule |
| Main visual | Center, large area | Replaceable vintage poster illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Decorative border | Full frame | Retro double-line geometric border, aged ink |

**Layout prohibitions:** No glossy modern gradients, no neon, no 3D renders, no pure-white sterile backgrounds. Keep the warm aged-paper atmosphere throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | American vintage poster画报, warm sepia caramel tones, aged paper grain texture |
| Base color | Warm cream `#E8DCC8` |
| Texture | Old paper grain, subtle foxing, faded print ink, soft vignette |
| Main visual type | Vintage poster illustration (NOT photography, NOT 3D, NOT neon) |
| Date font | Oversized bold slab serif (vintage wood-type feel) |
| Weekday font | All-caps condensed serif, wide tracking |
| Title font | Bold serif Chinese (warm, slightly worn ink) |
| Auxiliary text | Thin serif, aged ink |
| Border | Retro geometric double-line frame in warm brown |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Warm brown base `#E8DCC8` | Tender green |
| Summer | Jun–Aug | Warm brown base `#E8DCC8` | Caramel orange |
| Autumn | Sep–Nov | Warm brown base `#E8DCC8` | Ochre / umber |
| Winter | Dec–Feb | Warm brown base `#E8DCC8` | Grey-brown |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** nostalgic, warm, storied; may carry a sense of timeless craftsmanship

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 时光印记  (4–8 chars)
{SUBTITLE}         e.g., 岁月沉淀的温润，藏在每一帧旧时光里  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., vintage botanical still-life poster illustration with caramel tones
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #E8DCC8
{ACCENT_COLOR}     e.g., caramel orange
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match vintage illustration by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#E8DCC8` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — vintage American poster style

A 9:16 vertical poster in vintage American poster style. Aged-paper grain, warm caramel-brown tones, retro geometric corner frames and double-line border. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom, all inside the double border):
- TOP-LEFT: A small retro emblem LOGO beside the English company name "{COMPANY_EN}" in condensed vintage sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in retro slab-serif with wide tracking.
- CENTER (large area): The main visual — a retro poster illustration: {MAIN_VISUAL_DESC}. Warm caramel tones, bold flat shapes, vintage halftone dot texture, aged-paper grain overlay. Colors limited to {BASE_COLOR} and {ACCENT_COLOR}.
- MID-LOWER: Main title "{MAIN_TITLE}" in bold condensed serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Aged warm cream ({BASE_COLOR}) with fine noise grain, slight vignette, and faint halftone print marks.

MOOD: Nostalgic, warm, vintage editorial. No promotional tone.

STYLE REFERENCES: 1950s American travel posters, WPA poster aesthetic, vintage botanical book illustration, aged paper texture, halftone print.

NEGATIVE: No photography, no 3D render, no high-saturation clashing colors, no cold tones, no smooth gradients, no modern flat design, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No neon, no glossy gradient, no 3D, no sterile white |
| 3 | Illustration style | Warm vintage poster illustration with aged-paper grain |
| 4 | Painting style | No cold modern flatness / no neon / no photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Warm sepia caramel palette present; not overly cold or bright |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in vintage poster style.
```

**Full variable call:**
```
Generate in vintage poster style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 时光印记
SUBTITLE: 岁月沉淀的温润，藏在每一帧旧时光里
MAIN_VISUAL_DESC: vintage botanical still-life poster illustration with caramel tones
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #E8DCC8
ACCENT_COLOR: caramel orange
```
