# Image Generation Prompt Skeletons — Index

> 8 reusable English prompt templates for the `GenerateImage` tool, one per poster style. Each follows a unified 9-section structure with `{VARIABLE}` placeholders.

---

## Quick Reference

| # | File | Style (EN) | Style (CN) | Core Visual | Main Visual Type |
|---|------|-----------|------------|-------------|-----------------|
| 01 | [01-album-minimalist.md](computer:///workspace/prompt-skeletons/01-album-minimalist.md) | Album Minimalist | 极素画册风 | Low-saturation ink landscape, faint paper texture | Ink-wash illustration |
| 02 | [02-geometric-composition.md](computer:///workspace/prompt-skeletons/02-geometric-composition.md) | Geometric Composition | 几何构成风 | Bauhaus hard-edge blocks, zero texture | Geometric illustration |
| 03 | [03-warm-retro.md](computer:///workspace/prompt-skeletons/03-warm-retro.md) | Warm Retro | 暖光复古风 | Aged paper, double border, earth-tone flat illustration | Flat geometric illustration |
| 04 | [04-light-shadow.md](computer:///workspace/prompt-skeletons/04-light-shadow.md) | Light & Shadow | 光影留白风 | Architectural photography, leader lines, color-block intervention | Architectural photography |
| 05 | [05-silent-humanist.md](computer:///workspace/prompt-skeletons/05-silent-humanist.md) | Silent Humanist | 静默人文风 | Architectural light/shadow, calligraphic title, three-band | Architectural photography |
| 06 | [06-tech-streamer.md](computer:///workspace/prompt-skeletons/06-tech-streamer.md) | Tech Streamer | 科技流光风 | 3D-rendered abstract graphics, ice-blue gradient, particles | 3D render |
| 07 | [07-ink-wash.md](computer:///workspace/prompt-skeletons/07-ink-wash.md) | New Chinese Ink Wash | 新中式水墨风 | Digital ink landscape, ruyi frame, bamboo, 4-layer depth | Digital ink-wash illustration |
| 08 | [08-paper-light-craft.md](computer:///workspace/prompt-skeletons/08-paper-light-craft.md) | Paper Light Craft | 晨光纸艺风 | Layered paper collage, pressed flower, window-light shadow | Paper-craft collage |

---

## Unified Structure (all 8 files)

Each skeleton contains 9 sections:

1. **Role & Identity** — designer persona and emotional core
2. **Canvas & Layout Skeleton** — 9:16 grid with ASCII diagram + zone table
3. **Visual Style Lock** — color, texture, typography, material specs
4. **Seasonal Color System** — Spring/Summer/Autumn/Winter palettes with HEX values
5. **Copywriting Rules** — title/subtitle length and tone
6. **Variable Placeholders** — `{VARIABLE}` list with examples + default fallbacks
7. **Full Prompt Template** — copy-paste block for `GenerateImage` (includes NEGATIVE prompt)
8. **Self-Check Checklist** — 6-item post-generation verification
9. **Usage Example** — minimal + full-variable call samples

---

## How to Use

1. Open the desired style file
2. Replace all `{VARIABLES}` in Section 6 with your content
3. Copy the Section 7 "Full Prompt Template" block
4. Paste into `GenerateImage` as the `prompt` parameter
5. After generation, verify against the Section 8 checklist

---

## Shared Defaults

All templates share these enterprise defaults (from `company-config.md`):

| Field | Value |
|-------|-------|
| Company (CN) | 珠海宏兹嘉华科技有限公司 |
| Company (EN) | HUNTZ ENTERPRISES |
| Address | 珠海市格力金琴健康港12栋 |
| Phone | 0756-8639917 |
| Email | hello@yourcompany.com |
| QR label | 扫码了解更多 |

All templates output **9:16 vertical** format with six fixed zones and a bottom contact-info + QR-code area following the global bottom spec (plain text, no icons, tight leading, QR at 15–18% zone width).
