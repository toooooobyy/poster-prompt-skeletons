# New Chinese Ink Wash Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the New Chinese Ink Wash poster specification (Template 07). Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **new-Chinese ink-wash landscape brand calendar poster designer** locked into a visual framework of digital ink-wash landscapes + traditional motifs + Zen whitespace. Your core emotion is Song-dynasty literati aesthetics and Eastern Zen. You produce 9:16 vertical posters for daily brand messaging, the 24 solar terms, and traditional-festival brand campaigns — emphasizing cultural depth and refined elegance, rejecting folkloric red-and-green saturation and promotional tone.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, **no enclosing border, whitespace-driven, 3:7 composition**:

```
┌─────────────────────────────┐
│ [LOGO]        ╭─────────╮    │
│              │ 节气标签  │   │  ← TOP ZONE
│              ╰─────────╯    │
│        竹枝 ↘ (ruyi frame)  │
│                             │
│      ░░░ 远山 ░░░           │
│    ▒▒▒ 中景 ▒▒▒             │  ← MAIN ZONE
│   ███ 近景 ███               │     (4-layer depth)
│   ▓▓ 坡地+孤松 ▓▓            │
│                             │
│ 标题（书法体）               │  ← BOTTOM ZONE
│ 副标题                       │
│ Contact        [QR CODE]    │
└─────────────────────────────┘
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO | Top-left | Geometric modern LOGO, small size |
| Solar-term label | Top-right | Solar-term / festival name inside a ruyi-cloud-head frame (four corners curl inward, double-line border) |
| Bamboo branch | Top-right edge | A bamboo branch slants in from outside the frame, white-outline + pale ink wash |
| Main visual | Center | Replaceable digital ink-wash landscape zone, four-layer depth, ~55% area, ~60% whitespace above |
| Title | Bottom-left | Main title (calligraphic kai/wei-bei script) + subtitle |
| Contact + QR | Bottom | Left: contact info; Right: QR code |

**Layout prohibitions:** No full-frame border; no full-bleed composition (whitespace must stay ~50–60%); no high-saturation folkloric colors; bamboo branch is a core identity element and cannot be removed.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | New Chinese ink wash — digital ink landscape + traditional motifs + Zen whitespace |
| Base color | Xuan-paper rice white / ivory `#F5F0E8`, fine texture noise, antique-book atmosphere |
| Main visual type | Digital ink-wash landscape illustration (NOT photography, NOT 3D, NOT flat geometric) |
| Four-layer depth | Distant mountains (boneless pale ink 30–40%) → midground (textured strokes 50–60%) → foreground (dense ink 80–100%) → ochre slope |
| Required elements | Pure-white sun circle (breathing anchor) + slope-side solitary pine (guest-welcoming pine silhouette) + bamboo branch breaking the edge |
| Ruyi-cloud frame | Solar-term label border, traditional auspicious motif, four corners curl inward, double-line |
| Texture simulation | Xuan-paper / silk-base texture + ink bleed (edge water-stain渗透) + mineral-pigment grain |
| Font · Solar-term label | Song / imitation-Song, inside ruyi frame |
| Font · Main title | Calligraphic kai / wei-bei script, stroke modulation, flying-white (飞白) |
| Font · Subtitle | Thin Song / imitation-Song |
| Font · Contact info | Modern sans-serif (hei-ti) |

---

## 4. Seasonal Color System (landscape hues shift with solar terms)

| Season | Landscape palette |
|--------|-------------------|
| Spring | Blue-green landscape + tender mineral green + pale apricot slopes |
| Summer | Cyan-blue landscape + deep azurite + ochre slopes |
| Autumn | Ochre-brown landscape + ochre dominant + caramel slopes |
| Winter | Pure ink-wash landscape + indigo cool tone + snow-white whitespace |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** Zen, elegant, solar-term reflection, cultural philosophy

---

## 6. Variable Placeholders

```
{SOLAR_TERM}       e.g., 立秋  (solar term or festival name)
{DATE_LABEL}       e.g., MON · 28 · JULY
{MAIN_TITLE}       e.g., 秋意渐浓  (4–8 chars)
{SUBTITLE}         e.g., 一叶知秋，静候岁月的回响  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., distant blue-green mountains fading into mist, a solitary pine on an ochre slope, pale sun circle upper right
{SEASON}           e.g., Autumn  (determines landscape palette)
{BASE_COLOR}       e.g., #F5F0E8
{LANDSCAPE_HUE}    e.g., blue-green + ochre
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {SOLAR_TERM} | Auto-match current solar term |
| {MAIN_TITLE} | Auto-generate from solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ink-wash elements by season |
| {SEASON} | Auto-detect from target month |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — new Chinese ink wash style, Song-dynasty literati aesthetics

A 9:16 vertical poster in new-Chinese ink-wash style. No enclosing border. Whitespace-driven 3:7 composition with ~50–60% blank space. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, landscape hue {LANDSCAPE_HUE}.

LAYOUT (top to bottom):
- TOP-LEFT: A small geometric modern LOGO mark.
- TOP-RIGHT: The solar-term label "{SOLAR_TERM}" set in Song/imitation-Song type, enclosed in a ruyi-cloud-head frame (traditional auspicious motif, four corners curling inward, double-line border).
- TOP-RIGHT EDGE: A bamboo branch slanting in from outside the frame, rendered in white-outline (白描) with pale ink wash. This is a core identity element — must be present.
- CENTER: The main visual — a digital ink-wash landscape: {MAIN_VISUAL_DESC}. Must have four-layer depth: distant mountains (boneless pale ink, 30–40% opacity) fading into mist, midground (textured strokes, 50–60%), foreground (dense ink, 80–100%), and an ochre slope. Must include a pure-white sun circle as a breathing anchor and a solitary pine on the slope (guest-welcoming pine silhouette). ~55% of canvas area, with ~60% whitespace above.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in calligraphic kai/wei-bei script with stroke modulation and flying-white (飞白), subtitle "{SUBTITLE}" in thin Song type below. Three lines of plain contact text (modern sans-serif, no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with the label "扫码了解更多" beneath it.

BACKGROUND: Xuan-paper rice white ({BASE_COLOR}) with fine texture noise and antique-book atmosphere. Ink-bleed edges with water-stain渗透 effect. Mineral-pigment grain.

MOOD: Song-dynasty literati, Zen, elegant, culturally deep. No folkloric saturation, no promotional tone.

STYLE REFERENCES: Song-dynasty landscape painting (郭熙, 范宽), digital ink-wash illustration, xuan-paper texture, traditional Chinese auspicious motifs, literati aesthetics.

NEGATIVE: No photography, no 3D render, no flat geometric design, no high-saturation red-green folkloric colors, no full-bleed composition, no full-frame border, no missing bamboo branch, no less than four depth layers, no calligraphy title replaced by modern font, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Bamboo & ruyi frame | Bamboo branch breaking edge + ruyi-cloud frame both present |
| 3 | Landscape depth | Must have four layers with atmospheric perspective |
| 4 | Color saturation | No garish/folkloric red-green; stay literati-elegant |
| 5 | Whitespace | ≥40% blank space; no clutter |
| 6 | Title font | Must use calligraphic kai/wei-bei (flying-white visible) |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in new Chinese ink wash style.
```

**Full variable call:**
```
Generate in new Chinese ink wash style:
SOLAR_TERM: 立秋
DATE_LABEL: MON · 28 · JULY
MAIN_TITLE: 秋意渐浓
SUBTITLE: 一叶知秋，静候岁月的回响
MAIN_VISUAL_DESC: distant blue-green mountains fading into mist, a solitary pine on an ochre slope, pale sun circle upper right
SEASON: Autumn
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
```
