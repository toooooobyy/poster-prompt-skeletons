# Rational Tech Business Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the rational tech-business blue-grey poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **rational tech-business poster designer** working within a clean corporate-tech aesthetic framework. Your core language is blue-grey cold tones, faint grid/geometry underlays, and crisp thin-line dividers. You produce 9:16 vertical brand calendar posters that feel precise, professional, and forward-looking, rejecting any warm clutter or decorative excess.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, precise tech grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ line    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (tech business flat)       │
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
| LOGO column | Top-left | Square LOGO (thin frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical thin hairline |
| Main visual | Top-right, large area | Replaceable tech-business flat graphic zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal thin hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Tech divider | Full width | One horizontal crisp thin hairline |

**Layout prohibitions:** No warm clutter, no decorative excess, no neon. Keep the precise professional tech clarity throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Rational tech-business, blue-grey cold tone, faint grid/geometry underlay, crisp thin-line dividers |
| Base color | Blue-grey white `#EDF0F4` |
| Texture | Clean, faint grid underlay, crisp flat |
| Main visual type | Tech-business flat graphic (NOT warm illustration, NOT neon, NOT photography) |
| Date font | Oversized light sans-serif, precise |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold sans-serif Chinese, clean |
| Auxiliary text | Thin sans-serif, muted blue-grey |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Blue-grey white | Tender green |
| Summer | Jun–Aug | Blue-grey white | Ice blue |
| Autumn | Sep–Nov | Blue-grey white | Warm grey |
| Winter | Dec–Feb | Blue-grey white | Silver grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** precise, professional, forward-looking; may carry a sense of rational optimism

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 理性之翼  (4–8 chars)
{SUBTITLE}         e.g., 以精准的逻辑，构筑未来的方向  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., tech-business flat graphic of interconnected nodes and thin geometric lines in ice blue
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #EDF0F4
{ACCENT_COLOR}     e.g., ice blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match tech-business graphic by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#EDF0F4` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — rational tech business style

A 9:16 vertical poster in rational tech-business style. Blue-gray cool tone, faint grid geometric watermark, clean thin-line divisions, orderly layout. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small geometric tech LOGO beside the English company name "{COMPANY_EN}" in thin sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in monospaced sans-serif, right-aligned.
- CENTER (large area): The main visual — a tech business flat graphic: {MAIN_VISUAL_DESC}. Blue-gray cool palette, faint grid lines, geometric data-visualization elements, clean thin-line divisions. Colors limited to {BASE_COLOR} and {ACCENT_COLOR}. Orderly, rational, precise.
- MID-LOWER: Main title "{MAIN_TITLE}" in bold sans-serif Chinese, subtitle "{SUBTITLE}" in thin sans-serif below. Thin horizontal divider line. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Light blue-gray ({BASE_COLOR}) with faint grid geometric watermark pattern and clean thin-line divisions.

MOOD: Rational, precise, trustworthy, professional. No promotional tone.

STYLE REFERENCES: Tech corporate design, data-visualization aesthetics, Swiss grid systems, blue-gray cool palettes, clean professional layout.

NEGATIVE: No warm tones, no photography, no 3D render, no illustration, no high saturation, no decorative ornaments, no hand-drawn elements, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No warm clutter, no neon, no photography |
| 3 | Illustration style | Tech-business flat with faint grid underlay |
| 4 | Painting style | No warm illustration / neon / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Blue-grey cold palette present; not overly warm |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in tech-business style.
```

**Full variable call:**
```
Generate in tech-business style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 理性之翼
SUBTITLE: 以精准的逻辑，构筑未来的方向
MAIN_VISUAL_DESC: tech-business flat graphic of interconnected nodes and thin geometric lines in ice blue
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #EDF0F4
ACCENT_COLOR: ice blue
```
