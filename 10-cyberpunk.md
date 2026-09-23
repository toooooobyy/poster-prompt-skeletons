# Cyberpunk Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the cyberpunk neon-noir poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **cyberpunk neon-noir poster designer** working within the futuristic dystopian aesthetic framework. Your core language is blue-purple cold-tone neon light, rainy-night hazy glow, and glitch-art texture. You produce 9:16 vertical brand calendar posters that feel futuristic, moody, and electric, rejecting any warm pastoral tone or flat sterile minimalism.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, neon-edged dark grid:

```
┌─────────────────────────────┐
│ [LOGO]  │  WEEKDAY          │
│ EN name │  DATE (large)     │  ← TOP ZONE
│         │  MONTH  │ glow    │
├─────────┤──────────────────┤
│                             │
│      MAIN VISUAL             │  ← MAIN ZONE
│   (cyberpunk city)           │
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
| LOGO column | Top-left | Square LOGO (dark bg + neon outline) + English company name |
| Date column | Top-left (below LOGO) | Weekday (uppercase, wide tracking) + oversized serif date numeral + month; vertical neon hairline |
| Main visual | Top-right, large area | Replaceable cyberpunk city illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese) + subtitle (thin sans-serif) + horizontal neon hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Neon divider | Full width | One horizontal glowing hairline |

**Layout prohibitions:** No warm pastel palettes, no pastoral natural scenery, no sterile flat white backgrounds. Keep the dark neon-noir atmosphere throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Cyberpunk neon-noir, blue-purple cold tone, rainy-night hazy light, glitch texture |
| Base color | Deep dark blue `#0A0E27` |
| Texture | Glitch art bands, scanlines, neon bloom, rain streaks, digital noise |
| Main visual type | Cyberpunk city illustration (NOT pastoral photography, NOT flat vector, NOT watercolor) |
| Date font | Oversized bold serif with neon glow + subtle glitch |
| Weekday font | All-caps monospace/tech sans, wide tracking |
| Title font | Bold serif Chinese with faint neon edge glow |
| Auxiliary text | Thin tech sans-serif, cool light tone |
| Light | Neon bloom, wet reflective streets, hazy fog |

---

## 4. Seasonal Color System

| Season | Months | Base | Neon accent |
|--------|--------|------|-------------|
| Spring | Mar–May | Deep blue base `#0A0E27` | Emerald green neon |
| Summer | Jun–Aug | Deep blue base `#0A0E27` | Magenta neon |
| Autumn | Sep–Nov | Deep blue base `#0A0E27` | Amber neon |
| Winter | Dec–Feb | Deep blue base `#0A0E27` | Ice-blue neon |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** futuristic, electric, moody; may carry a sense of neon-lit solitude

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 霓虹纪元  (4–8 chars)
{SUBTITLE}         e.g., 在雨夜的霓虹里，看见未来的脉搏  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., cyberpunk megacity skyline with magenta neon reflections on wet streets
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #0A0E27
{NEON_COLOR}       e.g., magenta neon
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match cyberpunk city scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#0A0E27` |
| {NEON_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — cyberpunk neon city style

A 9:16 vertical poster in cyberpunk style. Dark blue-purple cold tone, neon light effects, rainy-night atmosphere, glitch art elements. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, neon accent {NEON_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A small geometric neon-outline LOGO beside the English company name "{COMPANY_EN}" in thin futuristic sans-serif with glow effect.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in monospaced neon-glow type.
- CENTER (large area): The main visual — a cyberpunk city illustration: {MAIN_VISUAL_DESC}. Dark blue-purple base, neon glow accents ({NEON_COLOR}), rain streaks, reflective wet surfaces, holographic light leaks, subtle glitch artifacts. Dramatic high-contrast lighting.
- MID-LOWER: Main title "{MAIN_TITLE}" in bold futuristic sans-serif with neon glow, subtitle "{SUBTITLE}" in thin sans-serif below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Deep dark blue-purple ({BASE_COLOR}) with subtle rain texture, neon bokeh, and faint scan-line glitch.

MOOD: Futuristic, edgy, neon-lit, cinematic. No promotional tone.

STYLE REFERENCES: Blade Runner aesthetic, cyberpunk game key art, neon signage photography, glitch art, synthwave visuals.

NEGATIVE: No warm-tone palette, no daytime bright scenes, no flat 2D illustration, no soft pastel colors, no cartoon style, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No warm pastel, no pastoral scenery, no sterile white |
| 3 | Illustration style | Cyberpunk city with neon bloom, glitch, rain haze |
| 4 | Painting style | No pastoral / watercolor / flat vector tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Deep blue base with neon accent glow present; not overly bright or warm |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in cyberpunk style.
```

**Full variable call:**
```
Generate in cyberpunk style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 霓虹纪元
SUBTITLE: 在雨夜的霓虹里，看见未来的脉搏
MAIN_VISUAL_DESC: cyberpunk megacity skyline with magenta neon reflections on wet streets
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #0A0E27
NEON_COLOR: magenta neon
```
