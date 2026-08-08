# Campus Newsletter Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the campus newsletter / wild Word typography aesthetic. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **campus newsletter poster designer** working within the "wild Word typography" aesthetic framework — the visual language of early PC era (1995-2005) when ordinary people used Microsoft Word as their only design tool. Your core language is multi-font mixing, WordArt-style deformed titles, auto-shape decorations (stars, arrows, clouds, lines), information-dense layout with no whitespace, and Office default color palette. You produce 9:16 vertical brand calendar posters that feel sincerely clumsy, earnestly over-decorated, and unconsciously chaotic — the aesthetic of someone who tried very hard but didn't know design theory.

**Core principle — Sincere Clumsiness:** The chaos is NOT intentional. It comes from "I thought this looked good" — using multiple fonts means "I put effort into this," filling every space means "I finished the work," red+blue means "that's a nice combo." This is unconscious clutter, not anti-design rebellion.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, Word document layout feel:

```
┌─────────────────────────────┐
│ [LOGO]   │  WEEKDAY         │
│ EN name  │  DATE (large)    │  ← TOP ZONE
│ (small)  │  MONTH           │
├──────────┤──────────────────┤
│  ┌───┐   │   ┌───┐          │
│  │   │   │   │   │  ★ →     │  ← MAIN ZONE
│  │MAIN│  │  │side│          │    (column layout
│  │VIS │  │  │text│          │     with text boxes)
│  │   │   │   │   │          │
│  └───┘   │   └───┘   ☁      │
├──────────┤──────────────────┤
│ ═══════════════════════════ │
│  TITLE (WordArt style)      │  ← BOTTOM ZONE
│  Subtitle (bold sans)       │
│  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─   │
│  Contact │    [QR CODE]     │
└──────────┴──────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Small LOGO + English company name in sans-serif, left-aligned, small size |
| Date column | Top-right | Large date numeral + small weekday/month, uneven spacing (simulating space-bar alignment) |
| Main visual | Center (~40-50%) | Replaceable campus newsletter visual, may have side text boxes with quotes/slogans |
| Title area | Center-lower | Main title with WordArt-style deformation (arc/tilt/shadow/stretch), subtitle in bold sans-serif, horizontal line divider below |
| Contact info | Bottom-left | Plain text, no icons, small font, tight leading 1.1–1.2×, slight misalignment allowed |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |

**Layout characteristics:** Simulates Word column layout — side text boxes for quotes/slogans, auto-shape decorations (stars, clouds, arrows, small flowers) in corners, straight/dashed/wavy line dividers, overall information-dense "fill every space" visual.

**Layout prohibitions:** No smooth vector lines, no precise grid alignment, no large whitespace (empty areas must have decorative elements), no polished commercial finish, no single-font design (minimum 3 fonts), no Morandi/low-saturation palette.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Campus newsletter / wild Word typography, multi-font mixing, WordArt titles, auto-shape decorations, column layout, fill-every-space |
| Base color | Word default white `#FFFFFF` or slightly yellowed print paper `#FAFAF5` |
| Texture | Light laser-print grain, low-resolution image insertion feel (slight pixelation/blur), no premium texture |
| Color strategy | Office default palette: pure red `#FF0000`, pure blue `#0000FF`, pure yellow `#FFFF00`, pure green `#008000`, pure orange `#FF8C00` — uncalibrated raw colors |
| Layout logic | Space-bar alignment uneven spacing, column layout, free-floating text boxes, line/dashed-line dividers |
| Graphic language | Word auto-shapes: straight lines for borders, ovals/rectangles/stars/arrows/clouds as decoration, dashed/wavy lines as dividers, no gradients, only flat hard-edge shadows |
| Main visual type | Hand-drawn-feel flat illustration / low-res image insertion / simple drawing style |
| Date font | Large sans-serif, uneven spacing |
| Title font | WordArt-style — tilted/arc/stretched/shadow deformed, bold, vivid color |
| Subtitle font | Bold sans-serif, regular |
| Body/note font | Song/Kai style, small size |
| Contact font | Sans-serif, small, slight misalignment |

---

## 4. Seasonal Color System

| Season | Months | Main Color | Decoration Colors |
|--------|--------|------------|-------------------|
| Spring | Mar–May | Pure green `#008000` | Pure yellow `#FFFF00` / Pure red `#FF0000` |
| Summer | Jun–Aug | Pure blue `#0000FF` | Pure yellow `#FFFF00` / Pure green `#008000` |
| Autumn | Sep–Nov | Pure orange `#FF8C00` | Pure red `#FF0000` / Pure yellow `#FFFF00` |
| Winter | Dec–Feb | Pure blue `#0000FF` | Pure purple `#800080` / Pure cyan `#00FFFF` |

> Auto-detect: match by target month. August → Summer → blue main with yellow/green decoration.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** campus, nostalgic, everyday encouragement, youth literature, accessible positivity

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., FRI · 08 · AUGUST
{WEEKDAY}          e.g., FRIDAY
{DATE_NUMBER}      e.g., 08
{MONTH}            e.g., AUGUST
{MAIN_TITLE}       e.g., 青春纪事  (4–8 chars)
{SUBTITLE}         e.g., 在每个平凡的日子里，写下属于自己的故事  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., hand-drawn style illustration of students reading under a tree, flat colors, low-resolution feel
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{MAIN_COLOR}       e.g., #0000FF
{DECOR_COLOR_1}    e.g., #FFFF00
{DECOR_COLOR_2}    e.g., #008000
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match campus scene by season |
| {SEASON} | Auto-detect from target month |
| {MAIN_COLOR} | Match {SEASON} main color |
| {DECOR_COLOR_1} | Match {SEASON} decoration color 1 |
| {DECOR_COLOR_2} | Match {SEASON} decoration color 2 |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — campus newsletter / wild Word typography style, sincere clumsiness

A 9:16 vertical poster in campus newsletter style, simulating early PC era (1995-2005) wild Word typography aesthetic. Multi-font mixing (at least 3 different fonts), WordArt-style deformed title (tilted/arc/stretched/shadow), auto-shape decorations (stars, clouds, arrows, ovals, straight lines, dashed lines, wavy lines), information-dense layout with NO whitespace — every empty space filled with decorative elements or text. Office default color palette: uncalibrated pure reds, blues, yellows, greens. Light laser-print grain texture, low-resolution image feel. Sincere clumsiness — the chaos is unconscious, not intentional rebellion. Someone tried very hard but didn't know design theory. Flat 2D, no 3D, no photorealism.

SINCERE CLUMSINESS PRINCIPLE: The layout looks cluttered because the maker thought "more fonts = more effort" and "empty space = lazy." Space-bar alignment creates uneven spacing. Auto-shapes are stacked without layer management. WordArt titles are over-deformed. But everything is readable and earnestly made.

BASE: {SEASON} palette — main color {MAIN_COLOR}, decoration colors {DECOR_COLOR_1} and {DECOR_COLOR_2}.

LAYOUT (top to bottom, Word document feel):
- TOP-LEFT: Small LOGO + English company name "{COMPANY_EN}" in small sans-serif, left-aligned.
- TOP-RIGHT: Large date "{DATE_NUMBER}" + small weekday "{WEEKDAY}" and month "{MONTH}", uneven spacing simulating space-bar alignment.
- CENTER (~40-50%): The main visual — {MAIN_VISUAL_DESC}. Hand-drawn flat illustration style, low-resolution insertion feel. Side text boxes with quotes or slogans. Auto-shape decorations (stars ★, clouds ☁, arrows →, small flowers) scattered in corners and empty spaces. Colors: {MAIN_COLOR}, {DECOR_COLOR_1}, {DECOR_COLOR_2} in Office default palette.
- MID-LOWER: Main title "{MAIN_TITLE}" in WordArt-style deformed text (tilted/arc/stretched with hard shadow), subtitle "{SUBTITLE}" in bold sans-serif below. Horizontal straight or dashed line divider. Three lines of plain contact text (no icons, tight leading, slight misalignment):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.
- DECORATIONS: Straight-line borders around sections, stars/arrows/clouds in corners, dashed or wavy dividers between sections. Fill ALL empty spaces — no whitespace allowed.

MOOD: Nostalgic, campus, sincerely clumsy, earnestly over-decorated. The feeling of a student making their best effort with limited tools. Not anti-design, but pre-design.

STYLE REFERENCES: Early Microsoft Word documents (Office 97/2000/XP era), school newspaper layouts, classroom bulletin board drafts, WordArt clip art aesthetic, auto-shape decorations, print shop flyers, 1990s-2000s campus culture materials.

NEGATIVE: photorealistic, 3d render, smooth vector, professional grid system, minimalist whitespace, morandi palette, low saturation, polished commercial design, luxury aesthetic, single font, clean alignment, swiss design, international typographic style, gradients, soft shadows, depth of field, realistic perspective, promotional banners, emoji, icons in contact area.
```

---

## 8. Variant Prompts

### Variant A: Blackboard Bulletin (hand-drawn chalk feel)

Add to the standard prompt's style section:

```
BLACKBOARD BULLETIN VARIANT: Dark green chalkboard base #2D4A3E (or dark gray #3A3A3A). All text and graphics simulate chalk handwriting — white/yellow/pink chalk strokes, slightly rough edges. Auto-shapes become hand-drawn chalk style — wobbly lines, uneven stars. WordArt titles simulate colored chalk handwriting. Keep "sincere clumsiness" core but with handcraft warmth. No laser-print grain, replace with chalk dust texture.
```

### Variant B: Street Flyer (print shop style)

Add to the standard prompt's style section:

```
STREET FLYER VARIANT: More aggressive WordArt — oversized fonts, bold, tilted, heavy shadows, thick outlines. Stronger table/grid feel — simulate price list or schedule layout. Thick borders around all edges, corner arrows pointing to key info. More "vulgar" color combo — bright red+green+blue, zero whitespace, maximum information density. Simulate dot-matrix/laser print effect — uneven ink, slight misregistration. Anti-high-end, pure street-level commercial.
```

---

## 9. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Word typography feel | No smooth vector, has print grain and low-res feel |
| 3 | Auto-shape decorations | Stars/arrows/lines/clouds present as decorative elements |
| 4 | WordArt title | Main title has deformation (arc/tilt/shadow/stretch) |
| 5 | Multi-font mixing | At least 3 different font styles visible |
| 6 | Fill principle | No large whitespace — all areas have content or decoration |

---

## 10. Usage Example

**Minimal call:**
```
Generate today's daily poster in campus newsletter style.
```

**Variant calls:**
```
Generate in 校园小报风·黑板报 style: today's poster
Generate in 校园小报风·市井传单 style: today's poster
```

**Full variable call:**
```
Generate in campus newsletter style:
DATE_LABEL: FRI · 08 · AUGUST
WEEKDAY: FRIDAY
DATE_NUMBER: 08
MONTH: AUGUST
MAIN_TITLE: 青春纪事
SUBTITLE: 在每个平凡的日子里，写下属于自己的故事
MAIN_VISUAL_DESC: hand-drawn style illustration of students reading under a tree, flat colors, low-resolution feel
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
MAIN_COLOR: #0000FF
DECOR_COLOR_1: #FFFF00
DECOR_COLOR_2: #008000
```
