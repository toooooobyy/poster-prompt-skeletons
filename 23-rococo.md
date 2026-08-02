# Rococo Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Rococo macaron soft-pastel poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Rococo poster designer** working within the 18th-century French decorative aesthetic framework. Your core language is macaron-light soft pastels, graceful curling floral scrollwork, and delicate relief texture. You produce 9:16 vertical brand calendar posters that feel light, elegant, and romantic, rejecting any heavy darkness or harsh geometric flatness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, graceful decorative grid:

```
┌═════════════════════════════┐
║ [LOGO]  │  WEEKDAY          ║
║ EN name │  DATE (large)     ║  ← TOP ZONE
║         │  MONTH  │ scroll  ║
╠═════════════════════════════╣
║                             ║
║      MAIN VISUAL             ║  ← MAIN ZONE
║   (rococo decoration)        ║
║                             ║
╠═════════════════════════════╣
║ TITLE   │                  ║
║ Subtitle│   [QR CODE]      ║  ← BOTTOM ZONE
║ ─────── │                  ║
║ Contact │                  ║
╚═════════════════════════════╝
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Square LOGO (soft scrollwork frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical curling scrollwork |
| Main visual | Top-right, large area | Replaceable Rococo decorative illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal soft hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Scrollwork border | Full frame | Graceful curling floral relief border |

**Layout prohibitions:** No heavy darkness, no harsh geometric flatness, no neon. Keep the light romantic macaron softness throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Rococo, macaron-light soft pastels, graceful curling floral scrollwork, delicate relief texture |
| Base color | Soft pink-lilac `#E8D5E0` |
| Texture | Delicate relief, soft pastel, gentle decorative line |
| Main visual type | Rococo decorative illustration (NOT photography, NOT neon, NOT flat vector) |
| Date font | Oversized elegant serif, soft |
| Weekday font | All-caps thin serif, wide tracking |
| Title font | Bold elegant serif Chinese, soft ink |
| Auxiliary text | Thin serif, soft pastel tone |
| Motif | Graceful curling floral scrollwork (卷曲花纹) |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Pink base | Tender green |
| Summer | Jun–Aug | Blue base | Pink |
| Autumn | Sep–Nov | Apricot base | Brown |
| Winter | Dec–Feb | White base | Silver-blue |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** light, elegant, romantic; may carry a sense of gentle grace

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 柔光绮梦  (4–8 chars)
{SUBTITLE}         e.g., 在卷曲的花纹里，邂逅一缕温柔  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., rococo decorative illustration of curling floral scrollwork with pink and blue pastel relief
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #E8D5E0
{ACCENT_COLOR}     e.g., pink
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match rococo decoration by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#E8D5E0` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Rococo macaron soft-pastel scrollwork style

A 9:16 vertical poster in light Rococo style. Macaron-light soft pastels, graceful curling floral scrollwork, delicate relief texture, gentle decorative line. Six fixed zones with a curling floral relief border.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a soft scrollwork frame next to the English company name "{COMPANY_EN}" in elegant uppercase serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin serif with wide tracking, an oversized elegant serif numeral "{DATE_NUMBER}" (soft, visually dominant), and the month "{MONTH}" below. A vertical curling scrollwork divider runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Rococo decorative illustration: curling floral scrollwork, delicate relief, soft pastel tones. No photography, no neon, no flat vector.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold elegant serif Chinese (soft ink), subtitle "{SUBTITLE}" in thin serif below, followed by a horizontal soft hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small serif.
- FULL FRAME: A graceful curling floral scrollwork relief border.

MOOD: Light, elegant, romantic, gentle grace. No heavy darkness, no harsh geometric flatness.

STYLE REFERENCES: 18th-century French Rococo decoration, Jean-Honoré Fragonard pastels, curling floral relief, macaron soft palettes.

NEGATIVE: No heavy darkness, no harsh geometric flatness, no neon, no flat vector, no photography, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No heavy dark, no harsh geometry, no neon |
| 3 | Illustration style | Rococo scrollwork with macaron pastel relief |
| 4 | Painting style | No flat vector / neon / photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Soft macaron pastel palette present; not overly dark |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Rococo style.
```

**Full variable call:**
```
Generate in Rococo style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 柔光绮梦
SUBTITLE: 在卷曲的花纹里，邂逅一缕温柔
MAIN_VISUAL_DESC: rococo decorative illustration of curling floral scrollwork with pink and blue pastel relief
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #E8D5E0
ACCENT_COLOR: pink
```
