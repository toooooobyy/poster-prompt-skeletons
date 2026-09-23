# Japanese Ukiyo-e Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Japanese ukiyo-e woodblock poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **ukiyo-e woodblock poster designer** working within the traditional Japanese浮世绘 aesthetic framework. Your core language is woodblock print line work, Morandi-traditional color palettes, cloud-pattern motifs, and generous whitespace. You produce 9:16 vertical brand calendar posters that feel classical, elegant, and serene, rejecting any modern neon or photorealistic clutter.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, classical woodblock grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ cloud   │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (ukiyo-e woodblock)        │
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
| LOGO column | Top-left | Square LOGO (traditional frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical cloud-pattern divider |
| Main visual | Top-right, large area | Replaceable ukiyo-e woodblock illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Traditional divider | Full width | One horizontal thin line with cloud motif |

**Layout prohibitions:** No modern neon, no photorealistic clutter, no heavy 3D. Keep the classical woodblock elegance with generous whitespace throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Ukiyo-e woodblock print, Morandi-traditional colors, cloud patterns, generous whitespace |
| Base color | Rice-paper cream `#F5F0E8` |
| Texture | Woodblock grain, flat ink, traditional paper |
| Main visual type | Ukiyo-e woodblock illustration (NOT photography, NOT neon vector, NOT 3D) |
| Date font | Oversized brush serif, classical |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold brush serif Chinese, ink |
| Auxiliary text | Thin sans-serif, muted |
| Motif | Cloud patterns (雲紋) and traditional line work |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Rice-paper base | Cherry pink |
| Summer | Jun–Aug | Rice-paper base | Cyan-green |
| Autumn | Sep–Nov | Rice-paper base | Ochre-brown |
| Winter | Dec–Feb | Rice-paper base | Indigo |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** classical, elegant, serene; may carry a sense of seasonal poetic grace

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 浮世清欢  (4–8 chars)
{SUBTITLE}         e.g., 于留白之间，照见四时的风物  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., ukiyo-e woodblock print of waves and cyan-green hills with cloud motifs
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #F5F0E8
{ACCENT_COLOR}     e.g., cyan-green
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ukiyo-e scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#F5F0E8` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Japanese Ukiyo-e woodblock style

A 9:16 vertical poster in Ukiyo-e woodblock print style. Traditional Morandi-toned palette, cloud-pattern motifs, large whitespace, flat color planes with woodblock texture. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small traditional seal-style LOGO beside the English company name "{COMPANY_EN}" in thin serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in vertical Japanese-style serif.
- CENTER (large area): The main visual — a Ukiyo-e woodblock illustration: {MAIN_VISUAL_DESC}. Flat color planes, traditional cloud-pattern (雲紋) borders, woodblock grain texture, large whitespace above and below. Colors limited to {BASE_COLOR} and {ACCENT_COLOR}.
- MID-LOWER: Main title "{MAIN_TITLE}" in Mincho/Song serif Chinese, subtitle "{SUBTITLE}" in thin kai style below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Warm rice-paper white ({BASE_COLOR}) with faint woodblock grain and traditional cloud-pattern motifs in corners.

MOOD: Traditional, elegant, serene, culturally deep. No promotional tone.

STYLE REFERENCES: Hokusai and Hiroshige Ukiyo-e woodblock prints, traditional Japanese cloud patterns, Morandi-toned traditional colors, washi paper texture.

NEGATIVE: No photography, no 3D render, no high-saturation modern colors, no gradients, no modern flat design, no sharp geometric shapes, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No neon, no photorealism, no heavy 3D |
| 3 | Illustration style | Ukiyo-e woodblock with flat ink and cloud motifs |
| 4 | Painting style | No neon / photography / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Traditional palette with generous whitespace; not overly modern |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in ukiyo-e style.
```

**Full variable call:**
```
Generate in ukiyo-e style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 浮世清欢
SUBTITLE: 于留白之间，照见四时的风物
MAIN_VISUAL_DESC: ukiyo-e woodblock print of waves and cyan-green hills with cloud motifs
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #F5F0E8
ACCENT_COLOR: cyan-green
```
