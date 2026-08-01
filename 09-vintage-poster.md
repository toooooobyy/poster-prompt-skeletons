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
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
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
[PURPOSE]: Brand calendar poster — vintage American poster style, warm sepia caramel tones

A 9:16 vertical poster in warm vintage American poster画报 style. Aged paper grain texture, faded print ink, subtle foxing, soft vignette, and a retro double-line geometric border framing the whole poster. Six fixed zones with a thin divider rule.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a sepia frame next to the English company name "{COMPANY_EN}" in condensed uppercase serif with wide tracking.
- TOP-RIGHT: A date column — weekday "{WEEKDAY}" in all-caps condensed serif, an oversized bold slab-serif numeral "{DATE_NUMBER}" (vintage wood-type feel, visually dominant), and the month "{MONTH}" below. A thin divider rule separates it.
- CENTER (large area): The main visual — {MAIN_VISUAL_DESC}. Hand-rendered vintage poster illustration in warm sepia and caramel tones, aged paper texture, no glossy modern gradients, no neon, no photography.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (slightly worn warm ink), subtitle "{SUBTITLE}" in thin serif below, followed by a horizontal hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small serif.
- FULL FRAME: A retro double-line geometric border in warm brown.

MOOD: Nostalgic, warm, storied, timeless. No cold modern flatness, no promotional hard-sell.

STYLE REFERENCES: Mid-20th-century American print画报, vintage travel posters, aged wood-type posters, warm sepia print.

NEGATIVE: No glossy gradients, no neon, no 3D renders, no sterile white background, no photography, no watercolor, no ink wash, no promotional text, no sale banners, no emoji, no icons in contact area.
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
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #E8DCC8
ACCENT_COLOR: caramel orange
```
