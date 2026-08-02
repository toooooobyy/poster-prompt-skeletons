# Baroque Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Baroque dark-gold poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Baroque poster designer** working within the 17th-century European dramatic aesthetic framework. Your core language is dark-gold relief scrollwork, strong chiaroscuro light-shadow contrast, a deep luxurious ground, and oil-paint texture. You produce 9:16 vertical brand calendar posters that feel grand, opulent, and dramatic, rejecting any flat modern minimalism or bright pastel softness.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, ornate dramatic grid:

```
┌═════════════════════════════┐
║ [LOGO]  │  WEEKDAY          ║
║ EN name │  DATE (large)     ║  ← TOP ZONE
║         │  MONTH  │ gold    ║
╠═════════════════════════════╣
║                             ║
║      MAIN VISUAL             ║  ← MAIN ZONE
║   (baroque oil texture)      ║
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
| LOGO column | Top-left | Square LOGO (gold relief frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical gold scrollwork |
| Main visual | Top-right, large area | Replaceable Baroque oil-texture zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal gold hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Ornate border | Full frame | Dark-gold relief scrollwork (卷草纹) border |

**Layout prohibitions:** No flat modern minimalism, no bright pastel softness, no neon. Keep the grand dramatic dark-gold opulence throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Baroque, dark-gold relief scrollwork, strong chiaroscuro, deep luxurious ground, oil-paint texture |
| Base color | Deep brown `#2A1F14` |
| Texture | Oil-paint brushwork, relief scrollwork, rich impasto |
| Main visual type | Baroque oil-texture illustration (NOT flat vector, NOT neon, NOT photography) |
| Date font | Oversized bold serif (classical, gilded) |
| Weekday font | All-caps classical serif, wide tracking |
| Title font | Bold serif Chinese, gilded ink |
| Auxiliary text | Thin serif, warm gold tone |
| Light | Strong chiaroscuro, single dramatic light source |

---

## 4. Seasonal Color System

| Season | Months | Base | Gold | Accent |
|--------|--------|------|------|--------|
| Spring | Mar–May | Deep brown base | Dark gold | Green |
| Summer | Jun–Aug | Deep brown base | Dark gold | Blue |
| Autumn | Sep–Nov | Deep brown base | Dark gold | Ochre |
| Winter | Dec–Feb | Deep brown base | Dark gold | Silver |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** grand, opulent, dramatic; may carry a sense of timeless grandeur

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 华章盛启  (4–8 chars)
{SUBTITLE}         e.g., 于光影交叠间，尽显典雅的恢宏  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., baroque oil-texture still-life of drapery and gold vessels with dramatic blue accent light
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #2A1F14
{GOLD_COLOR}       e.g., dark gold
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match baroque oil scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#2A1F14` |
| {GOLD_COLOR} | Dark gold |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Baroque dark-gold chiaroscuro oil-texture style

A 9:16 vertical poster in grand Baroque style. Dark-gold relief scrollwork (卷草纹), strong chiaroscuro light-shadow contrast, deep luxurious brown ground, oil-paint texture. Six fixed zones with a dark-gold scrollwork border.

BASE: {SEASON} color palette — base color {BASE_COLOR}, gold color {GOLD_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a gold relief frame next to the English company name "{COMPANY_EN}" in classical uppercase serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps classical serif with wide tracking, an oversized bold serif numeral "{DATE_NUMBER}" (gilded, visually dominant), and the month "{MONTH}" below. A vertical gold scrollwork divider runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Baroque oil-texture illustration: rich impasto, dramatic chiaroscuro, deep brown ground, gold accents. No flat vector, no neon, no photography.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (gilded ink), subtitle "{SUBTITLE}" in thin serif below, followed by a horizontal gold hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small serif.
- FULL FRAME: A dark-gold relief scrollwork (卷草纹) border.

MOOD: Grand, opulent, dramatic, timeless grandeur. No flat modern minimalism, no bright pastel softness.

STYLE REFERENCES: 17th-century European Baroque painting, Caravaggio chiaroscuro, gilded relief scrollwork, rich oil-paint texture.

NEGATIVE: No flat modern minimalism, no bright pastel softness, no neon, no flat vector, no photography, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No flat minimalism, no pastel, no neon |
| 3 | Illustration style | Baroque oil texture with chiaroscuro and gold scrollwork |
| 4 | Painting style | No flat vector / neon / photography tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Deep brown with dark-gold grandeur; not overly bright |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Baroque style.
```

**Full variable call:**
```
Generate in Baroque style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 华章盛启
SUBTITLE: 于光影交叠间，尽显典雅的恢宏
MAIN_VISUAL_DESC: baroque oil-texture still-life of drapery and gold vessels with dramatic blue accent light
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #2A1F14
GOLD_COLOR: dark gold
```
