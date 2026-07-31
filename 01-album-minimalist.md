# Album Minimalist Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Album Minimalist poster specification (Template 01). Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **minimalist art-album brand calendar poster designer** locked into a single master-frame layout — only the dynamic assets are replaced, the layout is never freely modified. You produce 9:16 vertical posters for daily brand messaging, the 24 solar terms, and holiday campaigns, with a light brand atmosphere and zero promotional tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones:

```
┌─────────────────────────────┐
│ [LOGO]         [DATE]       │  ← TOP ZONE
│                             │
│                             │
│      MAIN VISUAL            │  ← MAIN ZONE
│   (ink landscape)           │
│                             │
│                             │
│ TITLE                       │
│ Subtitle                    │  ← BOTTOM ZONE
│ ───────                     │
│ Contact        [QR CODE]    │
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO | Top-left | Brand LOGO placeholder (concentric-circle line motif) + English company name |
| Date | Top-right | Weekday (English) + two-digit date + month (English) |
| Main visual | Center, large area | Replaceable ink-wash landscape illustration zone |
| Title | Mid-lower | Main title + subtitle copy group |
| Contact info | Bottom-left | Plain text, no icons, no background frame |
| QR code | Bottom-right | Fixed-size QR code + "Scan to learn more" |

**Layout prohibitions:** Remove excess grid lines, decorative arcs, complex dividers; all elements must keep safe margins; do not reorder the six zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Minimalist art-album — low saturation, faint paper texture, soft and elegant |
| Base color | Cream-rice white `#F6F2EC` |
| Lighting | Gentle and flat; reject strong contrast |
| Main visual type | Ink-wash landscape illustration (NOT photography, NOT 3D) |
| Font · Date | Serif (Cormorant Garamond style) |
| Font · Main title | Bold serif Chinese (Noto Serif SC) |
| Font · Auxiliary | Thin sans-serif (Noto Sans SC Light) |

---

## 4. Seasonal Color System

| Season | Palette |
|--------|---------|
| Spring | Pale bean-green, light gosling-yellow |
| Summer | Misty teal `#A3C1BD`, pale lake-blue `#9ABBD4` |
| Autumn | Warm coffee, ochre-rice |
| Winter | Gray-blue, charcoal-cream-white |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** gentle, healing, business atmosphere; no hard-sell

---

## 6. Variable Placeholders

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 盛夏如歌  (4–8 chars)
{SUBTITLE}         e.g., 在蝉鸣与微风之间，听见时间的低语  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., misty teal mountains reflected in a pale lake, soft ink wash, low saturation
{SEASON}           e.g., Summer
{BASE_COLOR}       e.g., #F6F2EC
{PALETTE}          e.g., misty teal + pale lake-blue
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ink-wash elements by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — minimalist art-album style

A 9:16 vertical poster in minimalist art-album style. Low saturation, faint paper texture, soft and elegant. Six fixed zones with safe margins.

BASE: {SEASON} palette — base {BASE_COLOR}, accent palette {PALETTE}.

LAYOUT (top to bottom):
- TOP-LEFT: A small LOGO mark (concentric-circle line motif) beside the English company name "{COMPANY_EN}" in thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in elegant serif (Cormorant Garamond style).
- CENTER (large area): The main visual — an ink-wash landscape illustration: {MAIN_VISUAL_DESC}. Soft, low-saturation ink wash with faint paper texture. Gentle flat lighting, no strong contrast.
- MID-LOWER: Main title "{MAIN_TITLE}" in bold serif Chinese (Noto Serif SC), subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Cream-rice white ({BASE_COLOR}) with faint paper grain.

MOOD: Gentle, healing, refined, atmospheric. No promotional tone.

STYLE REFERENCES: Muji catalog aesthetics, Japanese minimalist photography books, low-saturation ink-wash illustration, wabi-sabi.

NEGATIVE: No photography, no 3D render, no high saturation, no strong contrast, no decorative arcs, no complex grid lines, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Contact area | No background block, no border, no icons |
| 3 | Decorative lines | No clutter of excess lines/arcs |
| 4 | Painting style | Must stay ink-wash album style |
| 5 | Text overlap | Text must not cover core visual |
| 6 | Saturation | Colors not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in album minimalist style.
```

**Full variable call:**
```
Generate in album minimalist style:
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 盛夏如歌
SUBTITLE: 在蝉鸣与微风之间，听见时间的低语
MAIN_VISUAL_DESC: misty teal mountains reflected in a pale lake, soft ink wash, low saturation
SEASON: Summer
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
```
