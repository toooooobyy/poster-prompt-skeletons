# Warm Retro Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Warm Retro poster specification (Template 03). Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **retro-warm wabi-sabi brand calendar poster designer** locked into an aged-paper texture and earth-tone flat-illustration framework. Your core emotion is warm everyday poetry. You produce 9:16 vertical posters for daily brand messaging, lifestyle brand campaigns, and seasonal greetings — emphasizing warmth and the trace of time, rejecting cold rigidity and promotional tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, **global double-line nested border**:

```
┌─────────────────────────────┐
│ ╔═════════════════════════╗ │
│ ║      [LOGO] top-center  ║ │  ← TOP ZONE
│ ║  [date]    │  [title]   ║ │
│ ╠═════════════════════════╣ │
│ ║                         ║ │
│ ║    MAIN VISUAL          ║ │  ← MAIN ZONE
│ ║   (flat illustration)   ║ │
│ ║                         ║ │
│ ╠═════════════════════════╣ │
│ ║ [subtitle]              ║ │
│ ║ Contact    [QR CODE]    ║ │  ← BOTTOM ZONE
│ ╚═════════════════════════╝ │
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO | Top-center | Small geometric symbol (hexagon outline) |
| Date + title | Upper area | Left: weekday + large serif date numeral; Right: "today's theme" + main title |
| Main visual | Center | Replaceable flat geometric illustration zone, with a thin horizontal line above and below |
| Subtitle | Below main visual | Subtitle copy |
| Contact info | Bottom-left | Plain text, no icons |
| QR code | Bottom-right | Fixed-size QR code + "Scan to learn more" |

**Border spec:** Outer line coffee-brown 1px + inner line pale-cream 1px, gap ~8–12px.

**Layout prohibitions:** Do not remove the double-line border; no arc decorations or gradient backgrounds; do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Retro-warm wabi-sabi — aged-paper texture, flat geometric illustration |
| Base color | Aged yellow-cream paper `#F5F0E6` |
| Texture | Global fine noise grain, slight edge vignette, simulating old paper |
| Border system | Double nested thin lines (outer coffee-brown + inner pale-cream) |
| Main visual type | Flat geometric illustration (NOT photography, NOT ink wash, NOT 3D) |
| Font · Date | Large serif (Didot/Bodoni), strong stroke contrast |
| Font · Main title | Song / Mincho, thin horizontal + thick vertical strokes |
| Font · Subtitle | Thin Song / kai, poetic feel |

---

## 4. Seasonal Color System

| Season | Base + Main + Accent |
|--------|---------------------|
| Spring | Yellow-cream base + tender olive-green + pale apricot |
| Summer | Yellow-cream base + caramel-orange `#C67B4B` + deep olive-green `#8B8B5E` |
| Autumn | Yellow-cream base + ochre-brown + caramel-orange |
| Winter | Yellow-cream base + gray-brown + warm-white |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** poetic, warm, everyday; with life philosophy

---

## 6. Variable Placeholders

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MAIN_TITLE}       e.g., 慢煮时光  (4–8 chars)
{SUBTITLE}         e.g., 把日子过成一首不急不缓的诗  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., a flat geometric illustration of a steaming coffee cup on a wooden table, warm earth tones
{SEASON}           e.g., Summer
{BASE_COLOR}       e.g., #F5F0E6
{MAIN_COLOR}       e.g., #C67B4B
{ACCENT_COLOR}     e.g., #8B8B5E
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
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
| {MAIN_VISUAL_DESC} | Auto-match flat-illustration elements by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — warm retro wabi-sabi style

A 9:16 vertical poster in retro-warm wabi-sabi style. Aged-paper texture with fine noise grain and slight edge vignette. A global double-line nested border (outer coffee-brown 1px + inner pale-cream 1px, 8–12px gap). Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, main color {MAIN_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom, all inside the double border):
- TOP-CENTER: A small geometric LOGO symbol (hexagon outline).
- UPPER AREA: Left side — weekday "{WEEKDAY}" + large serif date numeral "{DATE_NUMBER}" (Didot/Bodoni, strong stroke contrast). Right side — label "今日主题" + main title "{MAIN_TITLE}" in Song/Mincho (thin horizontal, thick vertical).
- CENTER: The main visual — a flat geometric illustration: {MAIN_VISUAL_DESC}. A thin horizontal line above and below the illustration. Colors limited to {BASE_COLOR}, {MAIN_COLOR}, {ACCENT_COLOR}. No perspective, no realism.
- BELOW MAIN VISUAL: Subtitle "{SUBTITLE}" in thin Song/kai type, poetic feel.
- BOTTOM-LEFT: Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Aged yellow-cream paper ({BASE_COLOR}) with fine noise grain and slight edge vignette simulating old paper.

MOOD: Warm, poetic, everyday, nostalgic. No cold rigidity, no promotional tone.

STYLE REFERENCES: Vintage botanical book illustration, wabi-sabi aesthetics, muted earth-tone palettes, aged paper texture, flat geometric illustration.

NEGATIVE: No photography, no 3D render, no ink wash, no cold gray tones, no high saturation, no gradient background, no missing double border, no arc decorations, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Double border | Both lines present (not reduced to single) |
| 3 | Paper texture | Aged-paper noise/vignette present |
| 4 | Painting style | No cold/watercolor/realistic drift |
| 5 | Text overlap | Text must not cover core visual |
| 6 | Saturation | Not overly vivid or overly cold-gray |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in warm retro style.
```

**Full variable call:**
```
Generate in warm retro style:
WEEKDAY: MONDAY
DATE_NUMBER: 28
MAIN_TITLE: 慢煮时光
SUBTITLE: 把日子过成一首不急不缓的诗
MAIN_VISUAL_DESC: a flat geometric illustration of a steaming coffee cup on a wooden table, warm earth tones
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
```
