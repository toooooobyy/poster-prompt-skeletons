# New Ugly Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the New Ugly poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **New Ugly poster designer** working within the anti-design aesthetic framework. Your core language is intentional imperfection, deliberately broken grid layout, high-saturation clashing colors, low-fidelity print texture, and raw hand-made quality. You produce 9:16 vertical brand calendar posters that feel deliberately chaotic, raw, and anti-establishment, rejecting any polished commercial aesthetic or minimalist refinement.

**Core principle — Controlled Chaos:** The six-zone layout skeleton stays fixed, but elements within each zone may deliberately misalign, overlap, stretch, distort, or spill across boundaries. Chaos is limited to the visual treatment layer — brand information (date, title, contact) must remain readable. "It looks like random layout, but you can still read it."

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones (positions locked, internal elements may chaos):

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (stretched) │  ← TOP ZONE
│ (tilted)│  MONTH (shifted)  │
├─────────┤──────────────────┤
│                             │
│   MAIN VISUAL (chaotic)     │  ← MAIN ZONE
│   rough collage / scribble  │     (may spill)
│                             │
├─────────┤──────────────────┤
│ TITLE (distorted)           │
│ Subtitle (overlapping)      │  ← BOTTOM ZONE
│ Contact  │   [QR CODE]      │
└─────────┴──────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | LOGO may tilt/stretch slightly + English company name in distorted sans-serif |
| Date column | Top-right | Weekday + date numeral (may stretch/compress, zero/negative letter-spacing, slight misalignment) + month |
| Main visual | Center | Replaceable New Ugly visual zone (~45-55%), elements may spill across boundaries |
| Title area | Center-lower | Main title (may distort/stretch/overlap but must be readable) + subtitle, hand-drawn scribble marks may interleave |
| Contact info | Bottom-left | Plain text, no icons, small font, tight leading 1.1–1.2×, slight misalignment allowed but must be readable |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |

**Layout prohibitions:** No completely unreadable text (must be "controlled chaos"); no smooth vector lines; no perfect symmetry; no polished commercial finish; no soft gradients; no minimalist whitespace aesthetic; no luxury feel. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | New Ugly, high-saturation clashing colors + raw hand-made texture + deliberately broken layout + low-fidelity print texture |
| Base color | Season-dependent bright base (not white/cream — saturated color base) |
| Texture | Photocopy grain noise + offset printing dot texture + low-fidelity scan texture + hand-drawn scribble marks / scratch lines / eraser marks |
| Color strategy | High-saturation clashing pairs, no soft gradient, banded color gradation, reject Morandi/low-sat/soft palettes |
| Layout logic | Deliberately break grid, ignore golden ratio, unbalanced framing, text may stretch/compress/overlap/misalign |
| Graphic language | Rough basic geometry (rectangles/circles/triangles), arrows/exclamation marks, intentional amateur feel |
| Main visual type | Rough collage illustration / hand-drawn scribble / low-fidelity xerox image (NOT refined illustration, NOT 3D, NOT photography) |
| Date font | Sans-serif, may stretch/distort, zero/negative letter-spacing, slight misalignment |
| Title font | Sans-serif, may distort/stretch/overlap but must be readable |
| Subtitle font | Sans-serif, may slightly distort |
| Contact font | Sans-serif, small size, slight misalignment allowed but must be readable |

---

## 4. Seasonal Color System

| Season | Months | Base | Clashing Pair |
|--------|--------|------|---------------|
| Spring | Mar–May | Bright yellow `#FFE500` | Green `#00CC44` / Magenta `#FF0099` |
| Summer | Jun–Aug | Black `#111111` | Cyan-blue `#00CCFF` / Orange `#FF8800` |
| Autumn | Sep–Nov | Off-white `#F5F0E8` | Tomato red `#FF3300` / Purple `#9900CC` |
| Winter | Dec–Feb | Gray `#999999` | Electric blue `#0044FF` / Neon green `#00FF44` |

> Auto-detect: match by target month. August → Summer → black base with cyan-blue/orange clash.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** rebellious, experimental, street-level, everyday absurdity, anti-establishment philosophy

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., FRI · 08 · AUGUST
{WEEKDAY}          e.g., FRIDAY
{DATE_NUMBER}      e.g., 08
{MONTH}            e.g., AUGUST
{MAIN_TITLE}       e.g., 乱中有序  (4–8 chars)
{SUBTITLE}         e.g., 在刻意的混乱里，找到野蛮生长的力量  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., rough collage of torn paper fragments with spray-paint shapes and overlapping text layers in clashing colors
{SEASON}           e.g., Summer  (determines clashing palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #111111
{CLASH_COLOR_1}    e.g., #00CCFF
{CLASH_COLOR_2}    e.g., #FF8800
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match New Ugly collage elements by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | Match {SEASON} base |
| {CLASH_COLOR_1} | Match {SEASON} clash pair |
| {CLASH_COLOR_2} | Match {SEASON} clash pair |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — New Ugly style, anti-design aesthetic, controlled chaos

A 9:16 vertical poster in New Ugly style. Intentional imperfection, deliberately broken grid layout, ignore golden ratio and symmetrical composition, unbalanced framing. Chaotic typography, distorted stretched text, overlapping text layers. Hand-drawn scribble marks, scratch lines, eraser marks, draft sketch traces. Rough collage splicing, uneven cropping, torn paper edges. Photocopy grain noise, offset printing dot texture, low-fidelity scanned texture. Harsh high-saturation clashing color palette, no soft gradient, banded color gradation. Reject minimalist aesthetic, reject clean vector smooth lines, reject perfect symmetrical composition, reject polished commercial aesthetic. Raw hand-made texture, amateur draft visual logic, anti-establishment graphic design style, flat 2D graphic poster style, no realistic lighting, no photorealism.

CONTROLLED CHAOS PRINCIPLE: Six zone positions are fixed, but elements within each zone may deliberately misalign, overlap, stretch, distort, or spill across boundaries. Brand information (date, title, contact) must remain readable — "it looks like random layout, but you can still read it."

BASE: {SEASON} palette — base {BASE_COLOR}, clashing colors {CLASH_COLOR_1} and {CLASH_COLOR_2}.

LAYOUT (top to bottom, positions fixed, internal chaos allowed):
- TOP-LEFT: A LOGO (may tilt/stretch slightly) beside the English company name "{COMPANY_EN}" in distorted sans-serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" (may stretch/compress, zero letter-spacing, slight misalignment) + month "{MONTH}".
- CENTER (~45-55%): The main visual — {MAIN_VISUAL_DESC}. Rough collage, hand-drawn scribble, low-fidelity xerox quality. Elements may spill across zone boundaries. Colors: {BASE_COLOR}, {CLASH_COLOR_1}, {CLASH_COLOR_2} in harsh clashing pairs. Photocopy grain, offset dot texture, scan noise throughout.
- MID-LOWER: Main title "{MAIN_TITLE}" in distorted sans-serif (may stretch/overlap but MUST be readable), subtitle "{SUBTITLE}" below. Hand-drawn scribble marks and scratch lines may interleave. Three lines of plain contact text (no icons, tight leading, slight misalignment allowed but readable):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

MOOD: Rebellious, raw, anti-establishment, amateur-but-intentional. Controlled chaos. No polished commercial feel.

STYLE REFERENCES: Takada Yui / Allright Graphics, New Ugly design movement, anti-design, street flyer aesthetic, photocopy zine culture, rough collage, intentionally imperfect typography.

NEGATIVE: photorealistic, 3d render, smooth vector, minimalist, swiss grid system, international typographic style, moiré soft colors, morandi palette, perfect composition, neat alignment, clean edges, symmetrical, polished commercial design, luxury aesthetic, sleek UI, glitchcore, weirdcore, vaporwave, pop art, bauhaus, clean sketch, professional refined artwork, soft shadow, depth of field, realistic perspective, soft gradient, promotional banners, emoji, icons in contact area.
```

---

## 8. Variant Prompts

### Variant A: Japanese New Ugly (Takada Yui school, restrained chaos)

Add to the standard prompt's style section:

```
JAPANESE NEW UGLY VARIANT: Restrained chaos. Subtle irregular typography, faint hand-drawn scribbles, casual snapshot collage, mild offset misalignment, faint scan grain. Muted clashing colors (reduce saturation conflict but keep clash logic). Subtle distorted sans-serif fonts. Empty unbalanced negative space. No over-saturated gaudy colors. Art exhibition poster graphic style. Flat 2D.

ADDITIONAL NEGATIVE: loud gaudy colors, busy overstuffed frame, street vulgar collage, chinese folk ugly style, heavy texture, thick graffiti strokes.
```

### Variant B: Chinese Local New Ugly (street-level, aggressive chaos)

Add to the standard prompt's style section:

```
CHINESE LOCAL NEW UGLY VARIANT: Aggressive chaos. Folk street advertisement visual logic. Aggressively overlapping text, rough spray-paint texture, coarse color collision, uneven print offset, messy manual text layout. Torn tape collage traces, low-resolution scan texture, untrimmed rough edges. Anti-high-end commercial packaging style. Zine independent print texture. Flat graphic print style.

ADDITIONAL NEGATIVE: japanese restrained new ugly, delicate lines, soft tones, gallery art style, minimalist blank space.
```

---

## 9. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Anti-refinement | No smooth vector, no polished commercial finish, no perfect symmetry |
| 3 | Print texture | Photocopy grain / offset dot / scan noise / hand-drawn scribble present |
| 4 | Color clash | High-saturation clashing pairs visible; no Morandi/low-sat/soft palette |
| 5 | Layout chaos | Deliberate imbalance, misalignment, stretching, overlap present |
| 6 | Readability | Text is "controlled chaos" — looks chaotic but is still readable |

---

## 10. Usage Example

**Minimal call:**
```
Generate today's daily poster in New Ugly style.
```

**Variant calls:**
```
Generate in 新丑风·日式克制 style: today's poster
Generate in 新丑风·中式市井 style: today's poster
```

**Full variable call:**
```
Generate in New Ugly style:
DATE_LABEL: FRI · 08 · AUGUST
WEEKDAY: FRIDAY
DATE_NUMBER: 08
MONTH: AUGUST
MAIN_TITLE: 乱中有序
SUBTITLE: 在刻意的混乱里，找到野蛮生长的力量
MAIN_VISUAL_DESC: rough collage of torn paper fragments with spray-paint shapes and overlapping text layers in clashing colors
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #111111
CLASH_COLOR_1: #00CCFF
CLASH_COLOR_2: #FF8800
```
