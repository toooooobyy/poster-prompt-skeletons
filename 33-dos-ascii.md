# DOS ASCII Retro Style — Image Generation Prompt Skeleton

> A reusable prompt template for the `GenerateImage` tool, based on the DOS-era ASCII character art poster specification. Replace all `{VARIABLES}` before use.

---

## 1. Role & Identity

You are a **DOS ASCII retro poster designer** working within the pure-character typography aesthetic framework. Your core language is ASCII characters and CJK box-drawing symbols (┃ ━ ┏ ┓ ┗ ┛ ╋ ═ ≈ ★ ■ ● ◆ ※), monospace fonts, terminal color schemes, and CRT display texture. You produce 9:16 vertical brand calendar posters that feel like early PC terminal screens or character-art Word documents — orderly, mechanical, nostalgic, geeky. You reject ALL graphic objects (no vector shapes, no lines tool, no rectangles, no gradients) — every visual element must be made of characters.

**Core principle — Characters Are Everything:** All borders, dividers, decorative patterns, and even the main visual are constructed entirely from ASCII characters and CJK symbols. The constraint of "no graphics" is not a limitation but the defining aesthetic — order emerges from character grids, beauty from monospace repetition.

---

## 2. Canvas & Layout Skeleton

**Canvas:** 9:16 vertical (e.g., 1080×1920px)

Six fixed zones, ALL wrapped in character-drawn borders:

```
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ [LOGO]        WEEKDAY        ┃
┃ EN name       DATE · MONTH   ┃  ← TOP ZONE
┠───────────────────────────────┨
┃                               ┃
┃    ██████  ██  ██  ██████     ┃
┃    ██  ██  ██  ██  ██  ██     ┃  ← MAIN ZONE
┃    ██████  ██████  ██  ██     ┃    (ASCII art)
┃    ██  ██  ██  ██  ██  ██     ┃
┃                               ┃
┠───────────────────────────────┨
┃  ┏━━━━━━━━━━━━━━━━━━━━━━━┓   ┃
┃  ┃    MAIN TITLE         ┃   ┃  ← BOTTOM ZONE
┃  ┗━━━━━━━━━━━━━━━━━━━━━━━┛   ┃
┃  Subtitle                     ┃
┃  ─────────────────────────    ┃
┃  Contact        [QR CODE]     ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
```

| Zone | Position | Content |
|------|----------|---------|
| LOGO column | Top-left | English company name in monospace, ALL CAPS, wrapped in character border |
| Date column | Top-right | Monospace date numeral + weekday, `═` or `─` underline divider |
| Main visual | Center (~40-50%) | Replaceable ASCII character art zone — all visuals made of characters |
| Title area | Center-lower | Main title wrapped in character border (e.g., `┏━━━━┓`), subtitle in monospace |
| Contact info | Bottom-left | Plain text, no icons, monospace, tight leading 1.1–1.2× |
| QR code | Bottom-right | 1:1 square, 15–18% of zone width + "扫码了解更多" |

**Layout characteristics:** Entire canvas simulates a DOS terminal or early Word character-art document. Outer border: `┏━━━━━━━━━━━━━━━━━━━━┓`. Internal dividers: `┃` vertical, `═══` horizontal. Corner and decoration spots: `★ ■ ● ◆ ≈ ※` symbols. Everything aligned to character grid — perfect mechanical order.

**Layout prohibitions:** No non-character graphic objects (no vector shapes, no line tool, no rectangles, no gradients), no photography/3D/illustration, no color gradients, no non-monospace fonts, no large whitespace (characters must fill structural framework), no smooth polished finish.

---

## 3. Visual Style Lock

| Dimension | Specification |
|-----------|---------------|
| Overall style | DOS ASCII retro, pure character typography, zero graphic objects, monospace, terminal color |
| Base color | Variant-dependent: black `#0A0A0A` / white `#F8F8F0` / dark blue `#000088` |
| Texture | CRT scanline texture + slight pixel grain + character glow effect (dark variants only) |
| Color strategy | Extreme monochrome or duochrome: black+green `#00FF00`, black+amber `#FFB000`, white+black `#000000`, dark blue+white |
| Layout logic | Pure character grid — all elements strictly monospace-aligned, characters as pixels, fixed chars-per-line, perfect mechanical order |
| Graphic language | ASCII character art: `┃━┏┓┗┛╋══` for borders/dividers, `★■●◆※≈` for decoration, `/\|-+` for patterns, characters arranged to form images |
| Main visual type | ASCII character art pattern — landscape/object/abstract formed by characters |
| Global font | Monospace (Courier New / Consolas / terminal font), ALL CAPS for English |
| Title font | Monospace bold, wrapped in character border |
| Date font | Monospace numerals, mechanical feel |
| Contact font | Monospace, small size |

---

## 4. Seasonal Color System

| Season | Months | Terminal Scheme |
|--------|--------|-----------------|
| Spring | Mar–May | Black base + phosphor green `#00FF00` + white emphasis |
| Summer | Jun–Aug | Dark blue base `#000088` + white `#FFFFFF` + cyan `#00FFFF` |
| Autumn | Sep–Nov | Black base + amber `#FFB000` + white emphasis |
| Winter | Dec–Feb | White base `#F8F8F0` + pure black `#000000` + dark gray `#444444` |

> Auto-detect: match by target month. August → Summer → dark blue base with white/cyan text.

---

## 5. Copywriting Rules

- **Main title:** 4–8 Chinese characters (or ALL CAPS English)
- **Subtitle:** single-line short sentence, 12–22 characters
- **Tone:** geeky, digital philosophy, code poetry, retro-tech nostalgia, terminal romanticism

---

## 6. Variable Placeholders

Replace each placeholder before generating:

```
{DATE_LABEL}       e.g., FRI · 08 · AUGUST
{WEEKDAY}          e.g., FRIDAY
{DATE_NUMBER}      e.g., 08
{MONTH}            e.g., AUGUST
{MAIN_TITLE}       e.g., 字符纪元  (4–8 chars)
{SUBTITLE}         e.g., 在0与1的间隙里，找到属于人类的诗意  (12–22 chars)
{MAIN_VISUAL_DESC} e.g., ASCII character art of a satellite orbiting Earth, made entirely of characters like /\()|-+*#
{SEASON}           e.g., Summer  (determines terminal color)
{COMPANY_EN}       e.g., STAR RING AEROSPACE TECHNOLOGY GROUP
{CONTACT_ADDRESS}  e.g., 地球同步轨道星环空间站集群
{CONTACT_PHONE}    e.g., 00-SR-227300
{CONTACT_EMAIL}    e.g., contact@starring-tech.space
{BASE_COLOR}       e.g., #000088
{TEXT_COLOR}       e.g., #FFFFFF
{ACCENT_COLOR}     e.g., #00FFFF
```

**Default fallbacks when a variable is missing:**

| Missing | Default |
|---------|---------|
| {DATE_LABEL} | Auto-format from system date |
| {MAIN_TITLE} | Auto-generate from theme/solar term (4–8 chars) |
| {SUBTITLE} | Auto-generate from theme (12–22 chars) |
| {MAIN_VISUAL_DESC} | Auto-match ASCII art scene by season |
| {SEASON} | Auto-detect from target month |
| {BASE_COLOR} | Match {SEASON} base |
| {TEXT_COLOR} | Match {SEASON} text color |
| {ACCENT_COLOR} | Match {SEASON} accent color |

---

## 7. Full Prompt Template (copy into GenerateImage)

```
[PURPOSE]: Brand calendar poster — DOS ASCII retro style, pure character typography, terminal aesthetic

A 9:16 vertical poster in DOS ASCII retro style. Pure character typography — ALL visual elements (borders, dividers, decorations, main visual) are made entirely of ASCII characters and CJK box-drawing symbols (┃ ━ ┏ ┓ ┗ ┛ ╋ ═ ≈ ★ ■ ● ◆ ※). Zero graphic objects — no vector shapes, no line tools, no rectangles, no gradients. Monospace font throughout, ALL CAPS English. Perfect character-grid alignment, mechanical order. CRT scanline texture, slight pixel grain, character glow on dark backgrounds. Terminal duochrome color scheme. Flat 2D, no 3D, no photorealism.

CHARACTERS ARE EVERYTHING PRINCIPLE: Every border is ┏━━━━┓, every divider is ═══ or ───, every decoration is ★ or ■ or ● or ◆, and the main visual is an ASCII art pattern formed by characters like /\()|-+*#. The constraint of "no graphics" IS the aesthetic — order emerges from character grids, beauty from monospace repetition.

BASE: {SEASON} terminal palette — base {BASE_COLOR}, text {TEXT_COLOR}, accent {ACCENT_COLOR}.

LAYOUT (top to bottom, all in character borders):
- OUTER BORDER: Full canvas wrapped in ┏━━━━━━━━━━━━━━━━━━━━━━━━━━┓ character border.
- TOP-LEFT (inside border): English company name "{COMPANY_EN}" in monospace ALL CAPS, small size.
- TOP-RIGHT (inside border): Date "{DATE_NUMBER}" in monospace + weekday "{WEEKDAY}" + month "{MONTH}", with ═══ underline divider.
- CENTER (~40-50%): The main visual — {MAIN_VISUAL_DESC}. Entirely made of ASCII characters forming a pattern/image. Surrounded by character-drawn frame. Colors: {TEXT_COLOR} and {ACCENT_COLOR} on {BASE_COLOR} background.
- MID-LOWER: Main title "{MAIN_TITLE}" wrapped in character border (┏━━━━━━━━┓), subtitle "{SUBTITLE}" in monospace below. ──── divider line. Three lines of plain monospace contact text (no icons, tight leading):
  地址：{CONTACT_ADDRESS}
  电话：{CONTACT_PHONE}
  邮箱：{CONTACT_EMAIL}
- BOTTOM-RIGHT: A small 1:1 QR code placeholder (15–18% of zone width) with "扫码了解更多" beneath it in monospace.
- DIVIDERS: Internal section dividers using ┠─────────────┨ or ═══ patterns.
- DECORATIONS: ★ ■ ● ◆ ※ symbols at section corners and empty grid positions.

MOOD: Geeky, nostalgic, orderly, mechanical, terminal romanticism. The feeling of an early PC user crafting beauty from character constraints. Retro-tech nostalgia, code poetry.

STYLE REFERENCES: DOS terminal screens, ASCII art archives, early Word character-art documents, IBM monochrome displays, BBS bulletin board art, ANSI art, retro computing aesthetics, green-screen/amber-screen terminals.

NEGATIVE: photorealistic, 3d render, smooth vector graphics, vector shapes, line tool, rectangle tool, gradient fill, color photograph, illustration, brush strokes, watercolor, oil painting, non-monospace font, proportional font, colorful palette, pastel colors, morandi palette, soft shadows, depth of field, realistic perspective, promotional banners, emoji, icons in contact area, minimalist whitespace, hand-drawn style.
```

---

## 8. Variant Prompts

### Variant A: Green-Screen Terminal (classic DOS)

Add to the standard prompt's style section:

```
GREEN-SCREEN TERMINAL VARIANT: Pure black base #0A0A0A with phosphor green characters #00FF00. Prominent CRT scanline texture, characters with slight green phosphor glow. Simulates early IBM 5151 monochrome display. Maximum DOS purity. White used only for critical emphasis.
```

### Variant B: White Document (Word character-art)

Add to the standard prompt's style section:

```
WHITE DOCUMENT VARIANT: White base #F8F8F0 with pure black characters #000000. No CRT scanlines — replace with light laser-print grain (simulates printed Word document). Use full-width CJK box-drawing characters (┏━┓┃┗┛) instead of half-width (+-+|). More refined, gentle, everyday office document feel. Dark gray #444444 for secondary text.
```

### Variant C: Amber Terminal (warm retro)

Add to the standard prompt's style section:

```
AMBER TERMINAL VARIANT: Pure black base #0A0A0A with amber characters #FFB000. CRT scanlines + warm amber phosphor glow. Simulates early IBM 5153 amber monochrome display. Warmer and more nostalgic than green-screen. White used only for critical emphasis.
```

---

## 9. Self-Check Checklist

After generation, verify each item. Re-generate if any fails:

| # | Check Item | Pass Criteria |
|---|-----------|---------------|
| 1 | LOGO & QR code | Original aspect ratio, position unchanged |
| 2 | Pure character art | NO graphic objects — all visuals made of ASCII/symbols |
| 3 | Character borders | ┏━━┓ / ┃ / ═══ character structure framework present |
| 4 | Monospace font | Global monospace, mechanical order |
| 5 | Color limit | Maximum 2 colors (terminal duochrome), no color gradients |
| 6 | CRT/print texture | Scanlines (dark variants) or print grain (white variant) present |

---

## 10. Usage Example

**Minimal call:**
```
Generate today's daily poster in DOS ASCII retro style.
```

**Variant calls:**
```
Generate in DOS字符画·绿屏终端 style: today's poster
Generate in DOS字符画·白底文档 style: today's poster
Generate in DOS字符画·琥珀终端 style: today's poster
```

**Full variable call:**
```
Generate in DOS ASCII retro style:
DATE_LABEL: FRI · 08 · AUGUST
WEEKDAY: FRIDAY
DATE_NUMBER: 08
MONTH: AUGUST
MAIN_TITLE: 字符纪元
SUBTITLE: 在0与1的间隙里，找到属于人类的诗意
MAIN_VISUAL_DESC: ASCII character art of a satellite orbiting Earth, made entirely of characters like /\()|-+*#
SEASON: Summer
COMPANY_EN: STAR RING AEROSPACE TECHNOLOGY GROUP
CONTACT_ADDRESS: 地球同步轨道星环空间站集群
CONTACT_PHONE: 00-SR-227300
CONTACT_EMAIL: contact@starring-tech.space
BASE_COLOR: #000088
TEXT_COLOR: #FFFFFF
ACCENT_COLOR: #00FFFF
```
