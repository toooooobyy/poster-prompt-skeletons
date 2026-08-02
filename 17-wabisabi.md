# Wabi-sabi Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the wabi-sabi earth-tone poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **wabi-sabi poster designer** working within the Japanese aesthetic of imperfection and transience. Your core language is low-saturation earth tones, matte rough texture, and minimal natural elements. You produce 9:16 vertical brand calendar posters that feel raw, quiet, and grounded, rejecting any glossy perfection or ornate luxury.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, raw minimal grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ rough   │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (wabi-sabi abstract)       │
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
| LOGO column | Top-left | Square LOGO (rough frame) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical rough hairline |
| Main visual | Top-right, large area | Replaceable wabi-sabi natural abstract zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal rough hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Rough divider | Full width | One horizontal irregular hairline |

**Layout prohibitions:** No glossy perfection, no ornate luxury, no neon, no high saturation. Keep the raw matte imperfection throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Wabi-sabi, low-saturation earth tones, matte rough texture, minimal natural elements |
| Base color | Earth grey-white `#E8E2D9` |
| Texture | Matte rough plaster, handmade paper grain, irregular edges |
| Main visual type | Wabi-sabi natural abstract (NOT glossy photography, NOT neon, NOT ornate 3D) |
| Date font | Oversized irregular serif, raw |
| Weekday font | All-caps thin sans-serif, wide tracking |
| Title font | Bold serif Chinese, earthy ink |
| Auxiliary text | Thin sans-serif, muted |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Earth grey-white | Moss green |
| Summer | Jun–Aug | Earth grey-white | Withered green |
| Autumn | Sep–Nov | Earth grey-white | Ochre |
| Winter | Dec–Feb | Earth grey-white | Silver grey |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** raw, quiet, grounded; may carry a sense of impermanent beauty

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 侘寂之静  (4–8 chars)
{SUBTITLE}         e.g., 于残缺与粗粝中，照见本真的美  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., wabi-sabi abstract of a single rough ceramic vessel on matte plaster with moss-green shadow
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group（缩写：SRATG）
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #E8E2D9
{ACCENT_COLOR}     e.g., withered green
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match wabi-sabi abstract by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#E8E2D9` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — wabi-sabi earth-tone matte style

A 9:16 vertical poster in wabi-sabi style. Low-saturation earth tones, matte rough texture, irregular edges, minimal natural elements, handmade paper grain. Six fixed zones with an irregular rough divider.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a rough frame next to the English company name "{COMPANY_EN}" in thin uppercase sans-serif with wide letter-spacing.
- TOP-LEFT (below LOGO): A vertical date column — weekday "{WEEKDAY}" in all-caps thin sans-serif with wide tracking, an oversized irregular serif numeral "{DATE_NUMBER}" (raw, visually dominant), and the month "{MONTH}" below. A vertical rough hairline runs through this column.
- TOP-RIGHT (large area): The main visual — {MAIN_VISUAL_DESC}. Wabi-sabi natural abstract: matte rough texture, minimal elements, low-saturation earth tones, imperfection. No glossy photography, no neon, no ornate 3D.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (earthy ink), subtitle "{SUBTITLE}" in thin sans-serif below, followed by a horizontal rough hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small sans-serif.
- FULL WIDTH BOTTOM: A single horizontal irregular hairline.

MOOD: Raw, quiet, grounded, impermanent beauty. No glossy perfection, no ornate luxury.

STYLE REFERENCES: Japanese wabi-sabi interiors, handmade ceramic aesthetics, raw plaster and paper textures, imperfection-as-beauty philosophy.

NEGATIVE: No glossy perfection, no ornate luxury, no neon, no high saturation, no photography gloss, no 3D, no promotional text, no sale banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No gloss, no luxury, no neon, no high saturation |
| 3 | Illustration style | Wabi-sabi raw matte with minimal natural elements |
| 4 | Painting style | No glossy / neon / ornate tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Low-saturation earth palette present; not overly vivid |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in wabi-sabi style.
```

**Full variable call:**
```
Generate in wabi-sabi style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 侘寂之静
SUBTITLE: 于残缺与粗粝中，照见本真的美
MAIN_VISUAL_DESC: wabi-sabi abstract of a single rough ceramic vessel on matte plaster with moss-green shadow
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group（缩写：SRATG）
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #E8E2D9
ACCENT_COLOR: withered green
```
