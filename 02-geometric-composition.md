# Geometric Composition Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Bauhaus geometric composition poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **modernist geometric composition poster designer** working within the Bauhaus aesthetic framework. Your core language is rational geometric division and block composition — absolutely flat, zero texture, zero ornament. You produce 9:16 vertical brand calendar posters that emphasize order and power, rejecting any promotional or commercial tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, strict grid, no border:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ line    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (geometric composition)    │
│                             │
├─────────┤──────────────────┤
│ TITLE   │                  │
│ Subtitle│   [QR CODE]      │  ← BOTTOM ZONE
│ ─────── │                  │
│ Contact │                  │
├─────────┴──────────────────┤
│ ═══════════════════════════ │  ← bottom hairline
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Square LOGO (black bg + accent inner frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical 1px hairline through column |
| Main visual | Top-right, large area | Replaceable geometric composition illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal 1px hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "Scan to learn more" |
| Bottom hairline | Full width | One horizontal 1px line |

**Layout prohibitions:** No curves, no rounded corners, no gradients, no shadows, no drop shadows. All dividers must be 1px straight lines. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Bauhaus geometric composition, absolutely flat, zero texture |
| Base color | Cold gray / cement gray `#CFD0CE` |
| Block language | Rectangles, triangles, straight-line divisions, hard edges, no transitions |
| Main visual type | Geometric composition illustration (NOT photography, NOT ink wash, NOT 3D render) |
| Date font | Oversized bold serif (Didot/Bodoni style), visually dominant |
| Weekday font | All-caps sans-serif, wide tracking, thin weight |
| Title font | Bold serif Chinese (thin horizontal strokes, thick vertical strokes) |
| Auxiliary text | Thin sans-serif |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent | Block color |
|--------|--------|------|--------|-------------|
| Spring | Mar–May | Cold gray `#CFD0CE` | Tender green | Pure black `#000000` |
| Summer | Jun–Aug | Cold gray `#CFD0CE` | Terracotta orange `#C97B5A` | Pure black `#000000` |
| Autumn | Sep–Nov | Warm gray `#C8C4BC` | Ochre | Deep brown `#3A2A1A` |
| Winter | Dec–Feb | Silver gray `#D4D4D4` | Ice blue `#7BA7C9` | Charcoal `#2A2A2A` |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** rational, powerful, ordered; may carry philosophical reflection

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 秩序之美  (4–8 chars)
{SUBTITLE}         e.g., 在严谨的结构中，发现自由的力量  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., geometric architectural composition, rectangles and triangular blocks
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
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
| {MAIN_VISUAL_DESC} | Auto-match geometric elements by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — geometric composition style, Bauhaus aesthetic

A 9:16 vertical poster in strict Bauhaus geometric composition style. Absolutely flat, zero texture, zero gradient, zero shadow. The layout uses a rigid asymmetric grid with six fixed zones and a 1px bottom hairline spanning full width.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}, block color {BLOCK_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block (black background with a thin {ACCENT_COLOR} inner frame) next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized bold serif numeral "{DATE_NUMBER}" (Didot/Bodoni style, visually dominant), and the month "{MONTH}" below. A vertical 1px hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Pure geometric composition: rectangles, triangles, straight-line divisions, hard edges, no curves, no rounded corners. Colors limited to {BASE_COLOR}, {ACCENT_COLOR}, {BLOCK_COLOR}, and pure black/white. No perspective, no realistic detail, no photography.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (thin horizontal strokes, thick vertical strokes), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal 1px hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal 1px hairline.

MOOD: Rational, powerful, ordered. Bauhaus discipline. No promotional tone, no warmth, no softness.

STYLE REFERENCES: Bauhaus poster design, Josef Müller-Brockmann grid systems, Swiss International Typographic Style, hard-edge geometric abstraction.

NEGATIVE: No curves, no rounded corners, no gradients, no shadows, no drop shadows, no 3D effects, no photography, no ink wash, no watercolor, no organic shapes, no decorative ornament, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No gradient, no shadow, no curves, no rounded corners |
| 3 | Illustration style | No perspective, no realistic detail — pure flat hard-edge geometry |
| 4 | Painting style | No soft / watercolor / natural landscape tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Strong black-white contrast present; colors not overly soft |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in geometric composition style.
```

**Full variable call:**
```
Generate in geometric composition style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 秩序之美
SUBTITLE: 在严谨的结构中，发现自由的力量
MAIN_VISUAL_DESC: geometric architectural composition, rectangles and triangular blocks
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
```
