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
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
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
[PURPOSE]: Brand calendar poster — Vaporwave pink-purple-cyan retro-glow style

A 9:16 vertical poster in dreamy Vaporwave style. Pink-purple-cyan-blue neon gradients, retro soft-focus glow, scanline haze, retro grain, cyber-retro texture. Six fixed zones with a glowing neon divider hairline.

BASE: {SEASON} color palette — base gradient {BASE_COLOR}, accent gradient color {GRADIENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block (neon frame) next to the English company name "{COMPANY_EN}" in retro uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps retro sans-serif with wide tracking, an oversized bold serif numeral "{DATE_NUMBER}" with neon glow (visually dominant), and the month "{MONTH}" below. A vertical neon hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Vaporwave gradient graphic: pink-purple-cyan-blue gradients, retro soft-focus glow, scanline haze. No harsh realism, no flat vector, no watercolor.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese with faint neon edge, subtitle "{SUBTITLE}" in thin retro sans-serif below, followed by a horizontal neon hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small retro sans-serif.
- FULL WIDTH BOTTOM: A single horizontal glowing neon hairline.

MOOD: Dreamy, nostalgic, surreal, retro-future reverie. No harsh industrial realism, no sterile flat minimalism.

STYLE REFERENCES: 1980s/90s Vaporwave aesthetics, retro-future sunsets, neon gradient grids, surreal dreamlike glow.

NEGATIVE: No harsh industrial realism, no sterile flat white, no muted earth tones, no flat vector, no watercolor, no photography, no promotional text, no sale banners, no emoji, no icons in contact area.
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
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #FF71CE → #01CDFE
GRADIENT_COLOR: cyan-blue
```
