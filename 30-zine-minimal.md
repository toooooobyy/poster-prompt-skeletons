# ZINE Minimal Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the ZINE minimalist poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **ZINE minimalist poster designer** working within the quiet independent-ZINE aesthetic framework. Your core language is extreme whitespace (65–85% of canvas), tiny visual subject (8–25%), a single high-saturation color anchor (0.8–2.5% of canvas), and reproduction/scan imperfections. You produce 9:16 vertical brand calendar posters that feel quiet, poetic, archival, and deeply rooted in Japanese/Korean independent ZINE culture, rejecting any commercial advertising hierarchy or promotional noise.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, extreme-whitespace breathing layout:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (small)     │  ← TOP ZONE
│         │  MONTH            │
│                             │
│         ·                   │
│       ·   ·                 │  ← EXTREME WHITESPACE
│     [TINY VISUAL]           │  ← SUBJECT 8-25%
│         ·                   │
│         ·                   │
│                             │
│ TITLE                       │
│ Subtitle                    │  ← BOTTOM ZONE
│ ───────                     │
│ Contact  │   [QR CODE]      │
└─────────┴──────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Minimal line LOGO (small) + English company name in serif/typewriter face |
| Date column | Top-right | Weekday (small serif/mono, low contrast) + date numeral (small) + month; quiet, receding |
| Main visual | Center-upper | The only replaceable ZINE subject zone, occupying only 8–25% of canvas, surrounded by 65–85% paper whitespace |
| Title area | Center-lower | Main title (serif/typewriter) + subtitle; text may drift/press to edge |
| Contact info | Bottom-left | Plain text, no icons, tiny font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |

**Layout prohibitions:** No full-bleed scenes; no subject larger than 25% of canvas; no multi-color high saturation (single anchor only); no commercial advertising hierarchy; no 3D render, neon, cartoon style; no dense collage. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | ZINE minimalist, aged paper + extreme whitespace + tiny subject + single high-saturation anchor + reproduction/scan imperfections |
| Base color | Aged paper `#F0EBE3`, slightly yellowed/greyed paper surface with paper texture noise |
| Whitespace | 65–85% of canvas is paper surface whitespace; subject occupies only 8–25% |
| Subject type | Fragment / object / torn photo clipping / silhouette / solid color block / old printed illustration / specimen / texture window — a single visual metaphor, NOT a full scene |
| Subject treatment | Low contrast, xerox softening, torn edges, halftone, scan lines, risograph grain, xerox wear, ink bleed, slight misregistration — make the subject "belong to the paper" |
| Color logic | Paper color + grey/black support one high-saturation anchor; anchor occupies 0.8–2.5% of canvas or 15–35% of the visual composition; must be visible at thumbnail size; only ONE main high-saturation hue per image |
| Preferred hues | Cobalt blue / ultramarine primary, rotating cyan, purple, magenta-pink, lemon yellow, pear green, orange, tomato red |
| Forbidden descriptors | `near-monochrome`, `no strong accent`, `pale`, `muted`, `faded`, `pastel` (low-contrast descriptions allowed ONLY for paper surface and secondary ink) |
| Texture | Orthogonal scan appearance, matte absorbent paper, diffuse light, low-to-medium contrast, no hard shadows, no 3D depth; copy/stencil-print/halftone/letterpress/scan-paper imperfections |
| Date font | Small serif/monospace, low contrast, quietly receding |
| Title font | Serif/typewriter, restrained strokes, may drift/press to edge |
| Subtitle font | Thin serif/monospace, semi-readable, may include tiny date/location/weather/signature micro-text |
| Contact font | Monospace/sans-serif, extremely small, low contrast |

---

## 4. Seasonal Color System

| Season | Months | Paper Base | High-Saturation Anchor |
|--------|--------|------------|------------------------|
| Spring | Mar–May | Aged paper `#F0EBE3` | Pear green |
| Summer | Jun–Aug | Aged paper `#F0EBE3` | Cobalt blue |
| Autumn | Sep–Nov | Aged paper `#F0EBE3` | Tomato red |
| Winter | Dec–Feb | Aged paper `#F0EBE3` | Ultramarine |

> Auto-detect: match by target month. August → Summer → cobalt blue anchor.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** quiet, poetic, archival, diary-like, everyday philosophy
- **In-image text:** keep as short as possible (image models distort long text)

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 06 · AUGUST
{WEEKDAY}          e.g., WEDNESDAY
{DATE_NUMBER}      e.g., 06
{MONTH}            e.g., AUGUST
{MAIN_TITLE}       e.g., 纸上静默  (4–8 chars)
{SUBTITLE}         e.g., 在留白深处，听见一抹色彩的声音  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., a tiny torn-paper clipping of a bird silhouette with cobalt-blue ink spot, surrounded by vast paper whitespace
{SEASON}           e.g., Summer  (determines anchor color)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #F0EBE3
{ACCENT_COLOR}     e.g., cobalt blue
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ZINE subject by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#F0EBE3` |
| {ACCENT_COLOR} | Match {SEASON} anchor palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — ZINE minimalist style, quiet independent-ZINE aesthetic

A 9:16 vertical poster in ZINE minimalist style. Aged paper surface with paper texture noise. 65–85% of the canvas is quiet paper whitespace. A single tiny visual subject occupies only 8–25% of the canvas — a fragment, object, torn photo clipping, silhouette, or old printed illustration. One high-saturation color anchor (cobalt blue / ultramarine / pear green / tomato red per season) occupies 0.8–2.5% of the canvas, visible at thumbnail size. Reproduction imperfections: xerox softening, halftone, scan lines, risograph grain, ink bleed, slight misregistration. Matte absorbent paper, diffuse light, low-to-medium contrast, no hard shadows, no 3D depth.

BASE: {SEASON} palette — aged paper base {BASE_COLOR}, high-saturation anchor {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A minimal line LOGO (small, placed in whitespace) next to the English company name "{COMPANY_EN}" in small serif/typewriter face.
- TOP-RIGHT: Weekday "{WEEKDAY}" in small serif/monospace (low contrast, quietly receding), date numeral "{DATE_NUMBER}" (small), and month "{MONTH}" below.
- CENTER-UPPER (tiny zone): The main visual — {MAIN_VISUAL_DESC}. A single visual metaphor, NOT a full scene. The subject is treated with reproduction imperfections (xerox softening, halftone, scan lines, torn edges, risograph grain) to make it "belong to the paper." Surrounded by vast paper whitespace.
- CENTER-LOWER: Main title "{MAIN_TITLE}" in serif/typewriter (restrained strokes, may drift or press to edge), subtitle "{SUBTITLE}" in thin serif/monospace below. Keep in-image text SHORT.
- BOTTOM-LEFT: Three lines of plain contact text (no icons, no bullets, tiny font, tight leading 1.1–1.2×):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in tiny sans-serif.

MOOD: Quiet, poetic, archival, diary-like. Japanese/Korean independent ZINE aesthetic. No commercial advertising hierarchy, no promotional noise.

COLOR LOGIC: Paper color {BASE_COLOR} + grey/black support + ONE high-saturation anchor {ACCENT_COLOR}. The anchor must be visible at thumbnail size. Only one main high-saturation hue per image. Do NOT describe the overall image as low-saturation or monochrome — the paper and secondary ink are low-contrast, but the anchor is fully saturated.

STYLE REFERENCES: Japanese/Korean independent ZINE design, risograph print culture, xerox art, archival scan aesthetics, quiet editorial design, found-object collage.

NEGATIVE: No full-bleed scenes, no subject larger than 25% of canvas, no multi-color high saturation, no commercial advertising hierarchy, no product advertising, no 3D render, no neon, no cartoon style, no dense collage, no glossy mockup, no hard shadows, no near-monochrome overall description, no pale/muted/pastel overall description.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Whitespace ratio | 65–85% paper whitespace; subject 8–25% of canvas |
| 3 | Reproduction texture | Copy/scan/halftone/risograph imperfections present (no smooth digital surface) |
| 4 | Color anchor | Single high-saturation anchor visible at thumbnail size; occupies 0.8–2.5% of canvas; only one hue |
| 5 | Style violations | No 3D, neon, cartoon, commercial-ad hierarchy, or full-bleed scene |
| 6 | Text | Short in-image text; does not overlap core visual; no distortion from excessive length |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in ZINE minimalist style.
```

**Full variable call:**
```
Generate in ZINE minimalist style:
DATE_LABEL: WED · 06 · AUGUST
WEEKDAY: WEDNESDAY
DATE_NUMBER: 06
MONTH: AUGUST
MAIN_TITLE: 纸上静默
SUBTITLE: 在留白深处，听见一抹色彩的声音
MAIN_VISUAL_DESC: a tiny torn-paper clipping of a bird silhouette with cobalt-blue ink spot, surrounded by vast paper whitespace
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #F0EBE3
ACCENT_COLOR: cobalt blue
```
