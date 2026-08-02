# Silent Humanist Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Silent Humanist poster specification (Template 05). Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **silent-humanist brand calendar poster designer** locked into a framework of architectural light-and-shadow photography + calligraphic title typography + monochrome warm-tone three-band layout. Your core emotion is the power of stillness. You produce 9:16 vertical posters for daily brand messaging, brand personification, and professional-service industry campaigns — emphasizing humanistic warmth and de-advertised aesthetic trust, rejecting promotional tone and visual noise.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, **strict three-band layout, hairline dividers, no border**:

```
┌─────────────────────────────┐
│ [LOGO]         [DATE]       │  ← BAND 1: HEADER
│ ─────────────────────────── │  ← hairline
│                             │
│   ARCHITECTURE PHOTO        │  ← BAND 2: MAIN VISUAL
│   (light & shadow)          │     (~55%)
│                             │
│ ─────────────────────────── │  ← hairline
│ TITLE (calligraphic)        │  ← BAND 3: FOOTER
│ Subtitle                    │
│ Contact        [QR CODE]    │
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO | Header-left | Geometric single-line LOGO + Chinese company name + English name |
| Date | Header-right | Weekday (English) + date numeral, no frame, direct typesetting |
| Hairline | Below header | One horizontal hairline spanning the content area |
| Main visual | Center | Replaceable architectural/spatial photography zone, ~55% |
| Title | Bottom-left | Main title (calligraphic Song) + subtitle + hairline |
| Contact + QR | Bottom | Left: contact info; Right: QR code |

**Layout prohibitions:** No borders, no color-block interventions, no cold-color overlays, no leader-line annotations; the three-band hairline dividers cannot be omitted.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Silent humanist — architectural photography + calligraphic title + monochrome warm-tone three-band |
| Base color | Warm gray-white / cream `#F5F0E8`, simulating matte art paper |
| Main visual type | Real architectural / spatial photography (NOT illustration, NOT 3D) |
| Photography requirement | Low-saturation warm tone, golden-hour light, must include diagonal tree-shadow / light projection |
| Color strategy | Pure monochrome warm (cream → caramel-brown → deep-brown), absolutely no cold colors |
| Divider system | Two horizontal hairlines (below header + below title), pale-brown |
| Texture strategy | Deliberately "de-digitalized" — no gradient, no drop-shadow, no gloss |
| Font · Main title | Calligraphic Song (thin horizontal, thick vertical,撇捺 flying-white) |
| Font · Subtitle | Thin hei / round-hei |
| Font · Contact info | Standard hei |

---

## 4. Seasonal Color System (warm-value shifts, no cold colors introduced)

| Season | Base + Main tone + Tree-shadow color |
|--------|--------------------------------------|
| Spring | Warm cream base + tender-brown main + pale-green shadow |
| Summer | Warm cream base + caramel-brown main + deep-green shadow |
| Autumn | Warm cream base + ochre-brown main + warm-orange shadow |
| Winter | Warm cream base + gray-brown main + silver-gray shadow |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** restrained power, everyday philosophy, humanistic warmth

---

## 6. Variable Placeholders

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MAIN_TITLE}       e.g., 静默之力  (4–8 chars)
{SUBTITLE}         e.g., 在无声的光影中，听见建筑呼吸的节奏  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., golden-hour photograph of a concrete wall with diagonal tree-shadow projection, warm monochrome tone
{SEASON}           e.g., Summer
{BASE_COLOR}       e.g., #F5F0E8
{MAIN_TONE}        e.g., caramel-brown
{SHADOW_COLOR}     e.g., deep-green
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{COMPANY_CN}       e.g., 宏兹实业
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match architectural photography by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — silent humanist style, architectural light & shadow

A 9:16 vertical poster in silent-humanist style. Strict three-band layout with two horizontal hairline dividers (pale-brown), no enclosing border. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, main tone {MAIN_TONE}, tree-shadow color {SHADOW_COLOR}. Pure monochrome warm — absolutely no cold colors.

LAYOUT (three bands, top to bottom):
- BAND 1 (HEADER): Left — geometric single-line LOGO + Chinese company name "{COMPANY_CN}" + English name "{COMPANY_EN}". Right — weekday "{WEEKDAY}" + date "{DATE_NUMBER}", no frame, direct typesetting. Below the header: a horizontal hairline spanning the content area.
- BAND 2 (MAIN VISUAL, ~55%): Architectural/spatial photography: {MAIN_VISUAL_DESC}. Low-saturation warm tone, golden-hour light. Must include diagonal tree-shadow or light projection. Deliberately de-digitalized — no gradient, no drop-shadow, no gloss. Matte art-paper feel.
- Below main visual: a second horizontal hairline.
- BAND 3 (FOOTER): Main title "{MAIN_TITLE}" in calligraphic Song (thin horizontal, thick vertical, flying-white visible), subtitle "{SUBTITLE}" in thin hei below. Three lines of plain contact text (standard hei, no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Warm gray-white/cream ({BASE_COLOR}) simulating matte art paper.

MOOD: Silent, powerful, humanistic, warm. No promotional tone, no visual noise.

STYLE REFERENCES: Tadao Ando architectural photography, Hélène Binet, golden-hour light studies, matte art-paper printing, calligraphic Chinese typography.

NEGATIVE: No illustration, no 3D render, no cold colors, no borders, no color-block interventions, no leader-line annotations, no gradient, no drop-shadow, no gloss, no missing tree-shadow/light direction, no non-calligraphic title font, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Borders/blocks | No border, no color block, no cold overlay |
| 3 | Light direction | Must have tree-shadow / directional light element |
| 4 | Title font | Must use calligraphic Song (flying-white visible) |
| 5 | Three-band dividers | Both hairlines present |
| 6 | Digital effects | No gradient, no drop-shadow, no gloss |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in silent humanist style.
```

**Full variable call:**
```
Generate in silent humanist style:
WEEKDAY: MONDAY
DATE_NUMBER: 28
MAIN_TITLE: 静默之力
SUBTITLE: 在无声的光影中，听见建筑呼吸的节奏
MAIN_VISUAL_DESC: golden-hour photograph of a concrete wall with diagonal tree-shadow projection, warm monochrome tone
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
COMPANY_CN: 宏兹实业
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
```
