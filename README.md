# Poster Prompt Skeletons — 海报提示词骨架库

> 33 套可复用的海报图像生成 Prompt 骨架，覆盖现代极简 / 复古经典 / 国风中式 / 欧式潮流 / 肌理氛围 / 商务氛围 / 实验前卫七大类别。每套模板遵循统一的九节结构，通过 `{VARIABLE}` 占位符注入内容。

**在线生成器（GitHub Pages）：** <https://toooooobyy.github.io/poster-prompt-skeletons/>

---

## 仓库构成

| 路径 | 说明 |
|------|------|
| `index.html` | 交互式 Prompt 生成器（单文件 Web 应用，日签/壁纸双模式、标签筛选、风格变体、日历选择） |
| `data/templates.json` | **单一事实源（SSOT）**：33 套模板的全部结构化数据（标签 / 示例 / 色系 / Prompt / 变体） |
| `tools/build.py` | 从 SSOT 重新生成 index.html 数据区、README 速查表、SKILL.md 标签矩阵，并同步根目录模板 Section 7；`--check` 用于一致性校验 |
| `01-*.md` … `33-*.md` | 33 套英文 Prompt 骨架（九节结构，详见下文） |
| `skill/` | Agent Skill 形态：`SKILL.md` 主配置 + `templates/` 中文七层规范 + `shared/` 全局规范 + `examples/` 样张 |

## Quick Reference（由 tools/build.py 生成，请勿手改）

<!-- QUICKREF:BEGIN -->
| # | File | Style (EN) | Style (CN) | Category | Core Visual |
|---|------|-----------|------------|----------|-------------|
| 01 | [01-album-minimalist.md](./01-album-minimalist.md) | Album Minimalist | 极素画册风 | 现代极简 | 低饱和度水墨风景、柔和纸张肌理、治愈素雅 |
| 02 | [02-geometric-composition.md](./02-geometric-composition.md) | Geometric Composition | 几何构成风 | 现代极简 | 包豪斯美学、硬边块面、黑白强对比、零肌理 |
| 03 | [03-warm-retro.md](./03-warm-retro.md) | Warm Retro | 暖光复古风 | 复古经典 | 做旧纸张质感、双层边框、大地色系扁平插画 |
| 04 | [04-light-shadow.md](./04-light-shadow.md) | Light & Shadow | 光影留白风 | 肌理氛围 | 建筑摄影、引线标注、色块介入、极大留白 |
| 05 | [05-silent-humanist.md](./05-silent-humanist.md) | Silent Humanist | 静默人文风 | 肌理氛围 | 建筑光影摄影、书法标题、单色暖调三段式 |
| 06 | [06-tech-streamer.md](./06-tech-streamer.md) | Tech Streamer | 科技流光风 | 商务氛围 | 3D渲染抽象图形、冰蓝渐变、粒子系统、体积光效 |
| 07 | [07-ink-wash.md](./07-ink-wash.md) | New Chinese Ink Wash | 新中式水墨风 | 国风中式 | 数字水墨山水、如意云头框、竹枝破边、禅意留白 |
| 08 | [08-paper-light-craft.md](./08-paper-light-craft.md) | Paper Light Craft | 晨光纸艺风 | 肌理氛围 | 层叠纸张撕裂毛边、压花植物、金色光源、窗格阴影 |
| 09 | [09-vintage-poster.md](./09-vintage-poster.md) | Vintage Poster | 复古美式Vintage画报风 | 复古经典 | 暖棕焦糖色调、旧纸张做旧颗粒、复古几何边框 |
| 10 | [10-cyberpunk.md](./10-cyberpunk.md) | Cyberpunk | 赛博朋克Cyberpunk | 肌理氛围 | 蓝紫冷调霓虹光效、雨夜朦胧光影、故障艺术glitch |
| 11 | [11-morandi.md](./11-morandi.md) | Morandi Texture | 莫兰迪肌理风 | 肌理氛围 | 低饱和灰调柔色、朦胧柔和色块、哑光纸张肌理 |
| 12 | [12-minimal.md](./12-minimal.md) | Minimal | 极简主义Minimal风 | 现代极简 | 大面积留白、单一主视觉、柔和干净底色 |
| 13 | [13-memphis.md](./13-memphis.md) | Memphis | 孟菲斯Memphis风 | 现代极简 | 高饱和撞色几何、圆点波浪线条、自由趣味构图 |
| 14 | [14-forest.md](./14-forest.md) | Forest Minimal | 自然森系简约风 | 现代极简 | 虚化绿植柔光背景、低饱和草木色系、清新自然 |
| 15 | [15-popart.md](./15-popart.md) | Pop Art | 波普Pop Art风 | 复古经典 | 粗黑轮廓线、高对比撞色、丝网印刷网点肌理 |
| 16 | [16-ukiyo-e.md](./16-ukiyo-e.md) | Ukiyo-e | 日式和风浮世绘 | 复古经典 | 浮世绘版画、莫兰迪传统色、云纹纹样、大量留白 |
| 17 | [17-wabisabi.md](./17-wabisabi.md) | Wabi-sabi | 侘寂Wabi-sabi风 | 复古经典 | 大地低饱和色系、哑光粗糙肌理、极简自然元素 |
| 18 | [18-republic.md](./18-republic.md) | Republic Era | 民国复古风 | 复古经典 | 泛黄宣纸、老式印刷颗粒、窗棂边框、竖排文字 |
| 19 | [19-newguofeng.md](./19-newguofeng.md) | New Guofeng | 新中式国风 | 国风中式 | 水墨晕染淡彩、简约山水竹叶祥云浅元素、青绿色系 |
| 20 | [20-guochao.md](./20-guochao.md) | Guochao | 国潮风 | 国风中式 | 传统纹样+粗几何色块、红金撞色、扁平化国风图案 |
| 21 | [21-vaporwave.md](./21-vaporwave.md) | Vaporwave | 蒸汽波Vaporwave | 欧式潮流 | 粉紫青蓝霓虹渐变、复古柔焦光效、赛博复古肌理 |
| 22 | [22-baroque.md](./22-baroque.md) | Baroque | 巴洛克风 | 欧式潮流 | 暗金浮雕卷草纹样、强烈光影对比、深色华贵基底 |
| 23 | [23-rococo.md](./23-rococo.md) | Rococo | 洛可可风 | 欧式潮流 | 马卡龙浅柔色系、柔婉卷曲花纹、细腻浮雕质感 |
| 24 | [24-handdrawn.md](./24-handdrawn.md) | Hand-drawn Flat | 肌理手绘扁平风 | 肌理氛围 | 柔和手绘笔触、纸张噪点肌理、低饱和色块 |
| 25 | [25-filmgrain.md](./25-filmgrain.md) | Film Grain | 胶片颗粒风 | 肌理氛围 | 胶片噪点肌理、暖调柔焦光影、虚化氛围感 |
| 26 | [26-blackgold.md](./26-blackgold.md) | Black Gold | 轻奢极简黑金商务 | 商务氛围 | 深蓝/深灰哑光基底、细金色线条点缀、克制留白 |
| 27 | [27-techbiz.md](./27-techbiz.md) | Tech Business | 理性科技商务风 | 商务氛围 | 蓝灰冷调、浅淡网格几何暗纹、利落细线分割 |
| 28 | [28-warmgold.md](./28-warmgold.md) | Warm Gold | 暖金温馨商务风 | 商务氛围 | 米金浅棕柔和底色、细碎微光金箔质感、柔和漫射光影 |
| 29 | [29-graybiz.md](./29-graybiz.md) | Premium Gray | 高级灰极简商务 | 商务氛围 | 全色系低饱和灰调基底、极简几何细线分区、大量留白 |
| 30 | [30-zine-minimal.md](./30-zine-minimal.md) | ZINE Minimal | ZINE极简风 | 肌理氛围 | 仿旧纸张、极大留白、极小主体、单点高饱和锚点、印刷瑕疵 |
| 31 | [31-new-ugly.md](./31-new-ugly.md) | New Ugly | 新丑风 | 实验前卫 | 高饱和撞色、粗糙手作质感、刻意打破排版规则、低保真印刷肌理 |
| 32 | [32-campus-newsletter.md](./32-campus-newsletter.md) | Campus Newsletter | 校园小报风 | 实验前卫 | 早期Word野生排版美学、多字体混用、艺术字标题、自选图形堆叠、填满版面 |
| 33 | [33-dos-ascii.md](./33-dos-ascii.md) | DOS ASCII Retro | DOS字符画复古风 | 实验前卫 | 纯ASCII/全角符号排版、零图形对象、等宽字体、终端单色配色、CRT扫描线质感 |
<!-- QUICKREF:END -->

---

## 统一结构（所有骨架）

每套骨架包含 9 个小节：

1. **Role & Identity** — 设计师人设与情绪内核
2. **Canvas & Layout Skeleton** — 9:16 栅格 + ASCII 版式图 + 分区表
3. **Visual Style Lock** — 色彩、肌理、字体、材质锁死规则
4. **Seasonal Color System** — 春/夏/秋/冬四季色系（含 HEX）
5. **Copywriting Rules** — 主标题 / 副标题字数与语气
6. **Variable Placeholders** — `{VARIABLE}` 清单、示例与兜底值
7. **Full Prompt Template** — 可直接粘贴给图像生成模型的完整 Prompt（含 NEGATIVE）
8. **Self-Check Checklist** — 6 项生成后自检
9. **Usage Example** — 最小调用与全变量调用示例

部分模板附带**风格变体**（如几何构成风含包豪斯原色 / 瑞士网格变体，新中式水墨风含写意笔触变体），共享版式骨架，仅微调视觉参数。

---

## 如何使用

**方式一：网页生成器（推荐）**
打开在线生成器 → 选风格 → 填变量（留空则 AI 即兴生成）→ 复制 Prompt。

**方式二：手工使用骨架**
1. 打开目标风格文件（见速查表）
2. 替换第 6 节列出的所有 `{VARIABLES}`
3. 复制第 7 节的完整 Prompt 块，粘贴给图像生成模型
4. 生成后按第 8 节自检清单逐项核对

**方式三：Agent Skill**
将 `skill/` 目录作为 Skill 加载，按 `skill/SKILL.md` 的指令格式调用（支持「用【风格代号·变体】生成今日日签」与标签筛选）。

---

## 企业占位信息

所有模板共享一套固定默认占位（可在网页端自由修改），定义见 `skill/shared/company-config.md`：

| 字段 | 默认值 |
|------|--------|
| Company (CN) | 星环地球航天科技集团 |
| Company (EN) | STAR RING AEROSPACE TECHNOLOGY GROUP |
| Address | 地球同步轨道星环空间站集群 |
| Phone | 00-SR-227300 |
| Email | contact@starring-tech.space |
| QR label | 扫码了解更多 |

所有模板输出 **9:16 竖版**，底部联系信息区遵循 `skill/shared/bottom-spec.md` 全局规范（纯文字无图标、紧凑行距、二维码占区域宽度 15–18%）。

---

## 开发：新增 / 修改一套模板

1. 只改 `data/templates.json`；
2. 运行 `python3 tools/build.py` 重新生成所有派生内容；
3. 运行 `python3 tools/build.py --check` 确认全部同步。

详细变更历史见 [CHANGELOG.md](./CHANGELOG.md)。
