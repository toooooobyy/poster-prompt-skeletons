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
{COMPANY_EN}       e.g., HUNTZ ENTERPRISES
{CONTACT_ADDRESS}  e.g., 珠海市格力金琴健康港12栋
{CONTACT_PHONE}    e.g., 0756-8639917
{CONTACT_EMAIL}    e.g., hello@yourcompany.com
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
[PURPOSE]: Brand calendar poster — Republic of China 民国 vintage style

A 9:16 vertical poster in Republic of China 民国 vintage style. Yellowed rice-paper background, old print grain, faded ink, subtle foxing, and a window-lattice (窗棂) border framing the whole poster. Six fixed zones with a thin divider rule.

BASE: {SEASON} color palette — base color {BASE_COLOR}, accent color {ACCENT_COLOR}.

LAYOUT (top to bottom):
- TOP-LEFT: A square LOGO block with a lattice frame next to the English company name "{COMPANY_EN}" in condensed uppercase serif with wide tracking.
- TOP-RIGHT: A date column — weekday "{WEEKDAY}" in all-caps condensed serif, an oversized bold serif numeral "{DATE_NUMBER}" (old-type feel, visually dominant), and the month "{MONTH}" below. A thin divider rule separates it.
- CENTER (large area): The main visual — {MAIN_VISUAL_DESC}. 民国-era print illustration with aged ink linework on yellowed paper. No photography, no neon, no 3D.
- BOTTOM-LEFT: Main title "{MAIN_TITLE}" in bold serif Chinese (vertical-set, aged ink), subtitle "{SUBTITLE}" in thin serif below, followed by a horizontal hairline. Below the hairline, three lines of plain contact text (no icons, no bullets, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder occupying 15–18% of the zone width, with the label "扫码了解更多" beneath it in small serif.
- FULL FRAME: A window-lattice (窗棂) border in aged brown.

MOOD: Historical, literary, old-world, bygone elegance. No modern neon, no sterile flat sterility.

STYLE REFERENCES: 民国-era newspaper and magazine illustrations, Shanghai calendar posters, old wood-type print, window-lattice traditional frames.

NEGATIVE: No modern neon, no sterile flat white, no glossy 3D, no photography, no watercolor, no promotional text, no sale banners, no emoji, no icons in contact area.
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
COMPANY_EN: HUNTZ ENTERPRISES
CONTACT_ADDRESS: 珠海市格力金琴健康港12栋
CONTACT_PHONE: 0756-8639917
CONTACT_EMAIL: hello@yourcompany.com
BASE_COLOR: #EDE4D0
ACCENT_COLOR: indigo
```
