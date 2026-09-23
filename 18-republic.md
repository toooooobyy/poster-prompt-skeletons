# Republic of China Vintage Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the Republic of China (民国) vintage poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **Republic of China vintage poster designer** working within the early-20th-century民国 print aesthetic framework. Your core language is yellowed rice paper, old print grain, window-lattice borders, and vertical-set text. You produce 9:16 vertical brand calendar posters that feel historical, literary, and old-world, rejecting any modern flat sterility or neon edge.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, window-lattice grid:

```
┌═════════════════════════════┐
║ [LOGO]  WEEKDAY · MONTH      ║
║ EN name DATE (large)         ║  ← TOP ZONE
║         ──────               ║
╠═════════════════════════════╣
║                             ║
║      MAIN VISUAL             ║  ← MAIN ZONE
║   (民国 print illustration)   ║
║                             ║
╠═════════════════════════════╣
║ TITLE (vertical)            ║
║ Subtitle                    ║  ← BOTTOM ZONE
║ ───────                     ║
║ Contact                     ║
║                  [QR CODE]  ║
╚═════════════════════════════╝
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | Square LOGO (lattice frame) + English company name |
| Date column | Top-right | Weekday + oversized serif date numeral + month; thin divider rule |
| Main visual | Center, large area | Replaceable民国 print illustration zone |
| Title area | Bottom-left | Main title (bold serif Chinese, vertical-set) + subtitle (thin serif) + horizontal hairline |
| Contact info | Bottom-left, lowest | Plain text, no icons, small font, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |
| Lattice border | Full frame | Window-lattice (窗棂) border, aged ink |

**Layout prohibitions:** No modern neon, no sterile flat white, no glossy 3D. Keep the yellowed-paper historical atmosphere throughout. Do not reorder zones.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | 民国 vintage, yellowed rice paper, old print grain, window-lattice border, vertical text |
| Base color | Yellowed cream `#EDE4D0` |
| Texture | Aged paper grain, faded print ink, subtle foxing |
| Main visual type | 民国-era print illustration (NOT photography, NOT neon, NOT 3D) |
| Date font | Oversized bold serif (old-type feel) |
| Weekday font | All-caps condensed serif, wide tracking |
| Title font | Bold serif Chinese, vertical-set, aged ink |
| Auxiliary text | Thin serif, aged ink |
| Border | Window-lattice (窗棂) frame in aged brown |

---

## 4. Seasonal Color System

| Season | Months | Base | Accent |
|--------|--------|------|--------|
| Spring | Mar–May | Yellowed base | Ink green |
| Summer | Jun–Aug | Yellowed base | Indigo |
| Autumn | Sep–Nov | Yellowed base | Ochre |
| Winter | Dec–Feb | Yellowed base | Grey ink |

> Auto-detect: match by target month. July → Summer.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** historical, literary, old-world; may carry a sense of bygone elegance

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., MON · 28 · JULY
{WEEKDAY}          e.g., MONDAY
{DATE_NUMBER}      e.g., 28
{MONTH}            e.g., JULY
{MAIN_TITLE}       e.g., 旧时风物  (4–8 chars)
{SUBTITLE}         e.g., 在泛黄的纸页间，重温一段旧光阴  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., 民国-era print illustration of a classical garden pavilion with indigo ink linework
{SEASON}           e.g., Summer  (determines color palette)
{COMPANY_EN}       e.g., Star Ring Aerospace Technology Group
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #EDE4D0
{ACCENT_COLOR}     e.g., indigo
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match民国 illustration by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | `#EDE4D0` |
| {ACCENT_COLOR} | Match {SEASON} palette |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — Republic-era vintage style

A 9:16 vertical poster in Republic-of-China-era vintage style. Yellowed xuan-paper base, old letterpress grain, window-lattice border frame, vertical typesetting elements. Six fixed zones.

BASE: {SEASON} palette — base {BASE_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom, all inside the window-lattice border):
- TOP-CENTER: A small traditional seal LOGO beside the English company name "{COMPANY_EN}" in old-style serif.
- TOP-RIGHT: Weekday "{WEEKDAY}" + date "{DATE_NUMBER}" + month "{MONTH}" in vertical old-style serif type.
- CENTER (large area): The main visual — a Republic-era newspaper illustration: {MAIN_VISUAL_DESC}. Vintage line-engraving style, old letterpress grain, muted earth-tone colors limited to {BASE_COLOR} and {ACCENT_COLOR}. Nostalgic aged feel.
- MID-LOWER: Main title "{MAIN_TITLE}" in vertical Mincho/Song serif Chinese, subtitle "{SUBTITLE}" in horizontal thin kai below. Three lines of plain contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it.

BACKGROUND: Yellowed xuan-paper ({BASE_COLOR}) with old letterpress noise grain and faint ink-bleed stains.

MOOD: Nostalgic, scholarly, vintage, cultural. No promotional tone.

STYLE REFERENCES: Republic-of-China-era newspaper illustration, old letterpress printing, window-lattice frame motifs, vintage xuan-paper texture, traditional Chinese seal design.

NEGATIVE: No photography, no 3D render, no high saturation, no modern flat design, no smooth gradients, no neon colors, no promotional banners, no emoji, no icons in contact area.
```

---

## 8. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Prohibited elements | No neon, no sterile white, no glossy 3D |
| 3 | Illustration style | 民国 print with aged ink on yellowed paper |
| 4 | Painting style | No neon / photography / 3D tendency |
| 5 | Text | Does not overlap the core visual |
| 6 | Color | Yellowed historical palette present; not overly modern or bright |

---

## 9. Usage Example

**Minimal call:**
```
Generate today's daily poster in 民国 vintage style.
```

**Full variable call:**
```
Generate in 民国 vintage style:
DATE_LABEL: MON · 28 · JULY
WEEKDAY: MONDAY
DATE_NUMBER: 28
MONTH: JULY
MAIN_TITLE: 旧时风物
SUBTITLE: 在泛黄的纸页间，重温一段旧光阴
MAIN_VISUAL_DESC: 民国-era print illustration of a classical garden pavilion with indigo ink linework
SEASON: Summer
COMPANY_EN: Star Ring Aerospace Technology Group
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #EDE4D0
ACCENT_COLOR: indigo
```
