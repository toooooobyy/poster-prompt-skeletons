# Light & Shadow Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Light & Shadow poster specification (Template 04). Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **neo-minimalist architectural-photography brand calendar poster designer** locked into a framework of architectural photography + leader-line annotations + color-block interventions. Your core language is light, shadow, and whitespace. You produce 9:16 vertical posters for daily brand messaging, brand identity, and architecture/design/cultural-creative industries — emphasizing quietude, sophistication, and de-advertised aesthetic communication, rejecting promotional tone and information clutter.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, **no border, pure whitespace-driven**:

```
┌─────────────────────────────┐
│ [LOGO]         [DATE]       │  ← TOP ZONE
│                             │
│   ┌──────────────┐          │
│   │ ARCHITECTURE │          │  ← MAIN ZONE
│   │  PHOTOGRAPHY │          │     (offset left, not full-bleed)
│   │  + lead lines │          │
│   └──────────────┘          │
│                             │
│ TITLE                       │  ← BOTTOM ZONE
│ Subtitle  ─────             │
│ Contact    [QR + blocks]    │
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO | Top-left | Small sans-serif English, left-aligned |
| Date | Top-right | Date numeral inside a thin-line rounded-rectangle frame, right-aligned |
| Main visual | Center, offset left | Replaceable architectural photography zone, ~55%, not touching edges |
| Title | Bottom-left | Main title + subtitle + short hairline (not full-width) |
| Contact info | Bottom-left, lowest | Plain text, no icons |
| QR code | Bottom-right | Fixed-size QR code + 1–2 cold-color geometric blocks overlaid above it |

**Layout prohibitions:** No borders of any kind; no full-bleed photography; no decorative arcs or gradient backgrounds; whitespace ratio ~35–40%.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | Neo-minimalist — architectural photography + leader-line annotation + color-block intervention |
| Base color | Warm-tone cream / oat `#F5F3EF`, fine paper noise |
| Main visual type | Real architectural / spatial photography (NOT illustration, NOT 3D) |
| Photography requirement | Low saturation, low contrast, slight faded look |
| Light anchor | Must include one circular light spot as the sole highlight element |
| Color-block intervention | 1–2 low-saturation cold-color geometric blocks stacked at bottom-right |
| Leader lines | 1–2 architectural leader-line annotations in the main visual area |
| Font · Date | Monospaced numerals inside a 1px thin-line rounded-rectangle frame |
| Font · Main title | Bold Song / large title Song |
| Font · Subtitle | Thin sans-serif |

---

## 4. Seasonal Color System (intervention-block color shifts by season)

| Season | Base + Intervention-block color |
|--------|--------------------------------|
| Spring | Warm cream base + tender-green block |
| Summer | Warm cream base + misty-blue block `#A8B4C4` |
| Autumn | Warm cream base + ochre-gray block |
| Winter | Warm cream base + ice-gray block |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** quiet, philosophical, spatial; may use architecture/time/light imagery

---

## 6. Variable Placeholders

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{DATE_NUMBER}      e.g., 28
{MAIN_TITLE}       e.g., 光之轨迹  (4–8 chars)
{SUBTITLE}         e.g., 在留白与结构之间，光影定义了空间的呼吸  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., low-angle photograph of a concrete staircase with soft directional light, faded look, single circular light spot
{SEASON}           e.g., Summer
{BASE_COLOR}       e.g., #F5F3EF
{BLOCK_COLOR}      e.g., #A8B4C4
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
| {MAIN_VISUAL_DESC} | Auto-match architectural photography by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — light & shadow neo-minimalist architectural style

A 9:16 vertical poster in neo-minimalist light & shadow style. No borders. Pure whitespace-driven layout (~35–40% blank). Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, intervention-block color {BLOCK_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: Company name "{COMPANY_EN}" in small sans-serif, left-aligned.
- TOP-RIGHT: Date numeral "{DATE_NUMBER}" inside a 1px thin-line rounded-rectangle frame, right-aligned.
- CENTER (offset left): The main visual — architectural/spatial photography: {MAIN_VISUAL_DESC}. Low saturation, low contrast, slight faded look. Must include one circular light spot as the sole highlight. The photo occupies ~55% of canvas, does NOT touch any edge (not full-bleed). May include 1–2 architectural leader-line annotations.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold Song/large-title Song, subtitle "{SUBTITLE}" in thin sans-serif below, followed by a short hairline (not full-width). Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: 1–2 low-saturation cold-color geometric blocks ({BLOCK_COLOR}) stacked, with a small 1:1 QR code placeholder (15–18% of zone width) and "扫码了解更多" beneath.

BACKGROUND: Warm-tone cream/oat ({BASE_COLOR}) with fine paper noise.

MOOD: Quiet, sophisticated, spatial, de-advertised. No promotional tone, no clutter.

STYLE REFERENCES: Kinfolk magazine, architectural digest minimalism, faded-film photography, Hélène Binet architectural photography, Swiss whitespace design.

NEGATIVE: No illustration, no 3D render, no ink wash, no borders, no full-bleed photography, no decorative arcs, no gradient background, no high-saturation blocks, no missing light-spot anchor, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Borders | No line-frame enclosing the full image |
| 3 | Main visual | Must be photographic (not illustration) |
| 4 | Color blocks | Intervention blocks present, not overly vivid |
| 5 | Whitespace | ≥30%; no clutter |
| 6 | Light anchor | Circular light spot present; text not covering it |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in light & shadow style.
```

**Full variable call:**
```
Generate in light & shadow style:
DATE_NUMBER: 28
MAIN_TITLE: 光之轨迹
SUBTITLE: 在留白与结构之间，光影定义了空间的呼吸
MAIN_VISUAL_DESC: low-angle photograph of a concrete staircase with soft directional light, faded look, single circular light spot
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
```
