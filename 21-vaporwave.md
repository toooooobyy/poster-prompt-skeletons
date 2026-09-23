# Vaporwave Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Vaporwave pink-purple-cyan poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Vaporwave poster designer** working within the retro-futuristic 1980s/90s aesthetic framework. Your core language is pink-purple-cyan-blue neon gradients, retro soft-focus glow, and cyber-retro texture. You produce 9:16 vertical brand calendar posters that feel dreamy, nostalgic, and surreal, rejecting any harsh industrial realism or sterile flat minimalism.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, retro-gradient grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ glow    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (vaporwave gradient)       │
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
| LOGO column | Top-left | Square LOGO (neon frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical neon hairline |
| Main visual | Top-right, large area | Replaceable vaporwave gradient graphic zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal neon hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Neon divider | Full width | One horizontal glowing hairline |

**Layout prohibitions:** No harsh industrial realism, no sterile flat white, no muted earth tones. Keep the dreamy surreal retro-glow throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Vaporwave, pink-purple-cyan-blue neon gradients, retro soft-focus glow, cyber-retro texture |
| Base color | Pink-purple gradient `#FF71CE` → `#01CDFE` |
| Texture | Soft-focus glow, scanline haze, retro grain, gradient bands |
| Main visual type | Vaporwave gradient graphic (NOT harsh realism, NOT flat vector, NOT watercolor) |
| Date font | Oversized bold serif with neon glow |
| Weekday font | All-caps retro sans-serif, wide tracking |
| Title font | Bold serif Chinese with faint neon edge |
| Auxiliary text | Thin retro sans-serif, glowing tone |
| Light | Soft neon bloom, retro sunset glow |

---

## 4. Seasonal Color System

| Season | Months | Base gradient | Accent |
|--------|--------|---------------|--------|
| Spring | Mar–May | Pink-purple | Tender green |
| Summer | Jun–Aug | Pink-purple | Cyan-blue |
| Autumn | Sep–Nov | Pink-purple | Orange-gold |
| Winter | Dec–Feb | Pink-purple | Ice-white |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** dreamy, nostalgic, surreal; may carry a sense of retro-future reverie

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 幻境回响  (4–8 chars)
{SUBTITLE}         e.g., 在粉紫霓虹里，重温一场旧梦  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., vaporwave gradient graphic of a retro sunset grid with palm silhouettes in pink-purple cyan-blue
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #FF71CE → #01CDFE
{GRADIENT_COLOR}   e.g., cyan-blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match vaporwave graphic by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#FF71CE` → `#01CDFE` |
| {GRADIENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Vaporwave style

A 9:16 vertical poster in Vaporwave style. Pink-purple-cyan-blue neon gradient, retro soft-focus light effects, cyber-retro texture, 80s/90s aesthetic. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, gradient {GRADIENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small retro-digital LOGO beside the English company name "{COMPANY_EN}" in thin retro sans-serif with neon glow.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in retro digital/monospaced type with glow.
- CENTER (large area): The main visual — a Vaporwave gradient graphic: {MAIN_VISUAL_DESC}. Pink-purple-cyan neon gradient ({GRADIENT_COLOR}), retro soft-focus glow, scan lines, grid horizon, Greek statue or palm silhouette elements, 80s/90s cyber-retro aesthetic. Dreamy, hazy, nostalgic.
- MID-LOWER: Main title "{MAIN_TITLE}" in bold retro sans-serif Chinese with neon glow, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Soft pastel gradient base ({BASE_COLOR}) with neon gradient overlay ({GRADIENT_COLOR}), scan lines, and retro grid.

MOOD: Dreamy, nostalgic, retro-futuristic, hazy. No promotional tone.

STYLE REFERENCES: Vaporwave aesthetic, 80s/90s retro digital art, Miami Vice color palette, synthwave gradients, retro Japanese city pop visuals.

NEGATIVE: No photography, no 3D render, no earth tones, no muted palette, no realistic illustration, no sharp clean lines, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No harsh realism, no sterile white, no muted earth |
| 3 | Illustration style | Vaporwave gradient with soft-focus retro glow |
| 4 | Painting style | No flat vector / watercolor / realism tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Pink-purple-cyan neon gradients present; not overly muted |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in Vaporwave style.
```

**Full variable call:**
```
Generate in Vaporwave style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 幻境回响
SUBTITLE: 在粉紫霓虹里，重温一场旧梦
MAIN_VISUAL_DESC: vaporwave gradient graphic of a retro sunset grid with palm silhouettes in pink-purple cyan-blue
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #FF71CE → #01CDFE
GRADIENT_COLOR: cyan-blue
```
