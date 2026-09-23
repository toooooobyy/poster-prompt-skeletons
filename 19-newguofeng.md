# New Chinese Guofeng Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the new Chinese-style (新中式国风) ink-wash poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **new Chinese-style poster designer** working within the contemporary ink-wash国风 aesthetic framework. Your core language is ink-wash diffusion with light color, minimalist mountains/bamboo/auspicious-cloud light elements, and a blue-green (青绿) color system. You produce 9:16 vertical brand calendar posters that feel contemporary yet classical, restrained and refined, rejecting any gaudy heavy ornament or photorealistic clutter.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, light ink-wash grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ cloud   │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (ink-wash light motif)     │
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
| LOGO column | Top-left | Square LOGO (ink frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical thin cloud line |
| Main visual | Top-right, large area | Replaceable new Chinese ink-wash light-element zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Ink divider | Full width | One horizontal thin ink hairline |

**Layout prohibitions:** No gaudy heavy ornament, no photorealistic clutter, no neon. Keep the light contemporary-classical ink-wash restraint throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | New Chinese国风, ink-wash diffusion with light color, minimalist light elements, blue-green system |
| Base color | Blue-green rice white `#EFF2EC` |
| Texture | Ink-wash diffusion, soft paper, light brush |
| Main visual type | New Chinese ink-wash light elements (NOT photography, NOT neon, NOT heavy oil) |
| Date font | Oversized brush serif, refined |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold brush serif Chinese, ink |
| Auxiliary text | Thin sans-serif, muted |
| Motif | Mountains, bamboo, auspicious clouds (祥云) as light accents |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Blue-green rice white | Tender green |
| Summer | Jun–Aug | Blue-green rice white | Cyan-green |
| Autumn | Sep–Nov | Blue-green rice white | Ochre-yellow |
| Winter | Dec–Feb | Blue-green rice white | Flower-blue (花青) |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** contemporary-classical, restrained, refined; may carry a sense of Eastern poetic clarity

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 山水清音  (4–8 chars)
{SUBTITLE}         e.g., 于淡墨晕染间，听见东方的清宁  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., new Chinese ink-wash of distant mountains and bamboo with cyan-green auspicious-cloud accents
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #EFF2EC
{ACCENT_COLOR}     e.g., cyan-green
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ink-wash elements by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#EFF2EC` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — New Chinese Guofeng style

A 9:16 vertical poster in New Chinese Guofeng style. Ink-wash light-color diffusion, minimal landscape elements (mountains, bamboo, auspicious clouds), blue-green tone palette, large whitespace. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small modern Chinese-style LOGO beside the English company name "{COMPANY_EN}" in thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in Song/imitation-Song serif.
- CENTER (large area, offset): The main visual — New Chinese ink light elements: {MAIN_VISUAL_DESC}. Soft ink-wash diffusion, minimal landscape motifs (distant mountains, bamboo leaves, auspicious cloud outlines), pale watercolor tints in {ACCENT_COLOR}. Large whitespace above. Gentle, no heavy ink.
- MID-LOWER: Main title "{MAIN_TITLE}" in calligraphic kai/Song Chinese, subtitle "{SUBTITLE}" in thin Song below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Pale blue-green rice-paper white ({BASE_COLOR}) with faint ink-wash diffusion and xuan-paper grain.

MOOD: Elegant, fresh, culturally modern, serene. No promotional tone.

STYLE REFERENCES: New Chinese ink-wash illustration, modern Guofeng design, traditional blue-green landscape (青绿山水), xuan-paper texture, minimal auspicious motifs.

NEGATIVE: No photography, no 3D render, no high-saturation folkloric red-gold, no heavy dense ink, no full-bleed composition, no modern flat geometric design, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No gaudy ornament, no neon, no photorealism |
| 3 | Illustration style | New Chinese ink-wash with light elements |
| 4 | Painting style | No heavy oil / neon / photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Blue-green light palette present; not overly gaudy |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in new Chinese 国风 style.
```

**Full variable call:**
```
Generate in new Chinese 国风 style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 山水清音
SUBTITLE: 于淡墨晕染间，听见东方的清宁
MAIN_VISUAL_DESC: new Chinese ink-wash of distant mountains and bamboo with cyan-green auspicious-cloud accents
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #EFF2EC
ACCENT_COLOR: cyan-green
```
