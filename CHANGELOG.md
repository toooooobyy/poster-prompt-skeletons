# Changelog

本项目所有重要变更均记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

---

## [Unreleased]

_暂无未发布变更。_

---

## [v4.2.0] - 2026-08-15

### Added — AI 即兴创作（留空 = AI 生成）
- **副标题 AI 生成**：副标题留空时，提示词自动注入 `[AI-composed subtitle]` 指令，由图像 AI 根据主标题即兴创作 12-22 字副标题
- **主视觉 AI 生成**：主视觉描述留空时，自动注入 `[AI-composed visual]` 指令，由 AI 根据主标题与副标题即兴创作符合模板风格的主视觉
- 输入框 placeholder 与提示徽章同步更新（「留空 = AI 根据标题生成」）

### Added — 副标题隐藏开关
- 副标题标签栏新增「隐藏副标题」checkbox
- 勾选后：输入框禁用并显示「已隐藏 · 提示词将不含副标题」徽章
- 生成提示词时注入 `LAYOUT OVERRIDE — NO SUBTITLE` 高优先级指令块，声明完全去除副标题并做留白补偿

### Added — 壁纸模式（Wallpaper Mode）
- 新增「日签模式 / 壁纸模式」顶部切换器
- 壁纸模式下提示词自动移除：企业 LOGO、公司名称、日期（星期/日期数字/月份/时间标签）、联系信息（地址/电话/邮箱）、二维码及「扫码了解更多」
- 实现机制（双保险）：日期与企业占位符替换为 `[none]` + 追加 `LAYOUT OVERRIDE — WALLPAPER MODE` 高优先级指令块，指示 AI 重新平衡 9:16 版式、扩大主视觉区域
- 壁纸模式下网页端内容变量仅保留：主标题、副标题（含 AI 生成与隐藏开关）、季节色系；其余表单区自动隐藏
- 预览元信息显示当前模式（🖼️ 壁纸模式 / 📅 日签模式）

### Changed
- 33 套模板源文件零改动，全部通过 `generatePrompt()` 运行时后处理实现，维护成本不变
- 版本号更新至 `v4.2.0`

### Tag
- `v4.2.0` → 本次提交 — AI 即兴创作 + 副标题隐藏开关 + 壁纸模式

---

## [v4.1.0] - 2026-08-09

### Added — 体验优化（主视觉描述体验重构）
- **灵感骰子（P0）**：新增 `VISUAL_POOLS` 词库，按模板类别分 5 组（场景叙事 / 抽象构成 / 纹理质感 / 氛围情绪 / 字符图案），点击「🎲 随机灵感」一键填充 4 字段并自动生成描述
- **结构拆解（P1）**：主视觉描述输入区新增 4 个结构化字段（主体 Who / 动作 How / 环境 Where / 氛围 Vibe）+ 1 个自由槽位（额外画面细节），将"大作文"变"搭积木"
- **动态句式库（P1）**：新增 `SENTENCE_PATTERNS` 按模板类型分 5 组句式骨架，放弃固定前缀拼接，避免画面趋同；支持「🔄 换句式」按钮保留已填词仅切换句式
- **风格联动示例（P1）**：为全部 35 套模板各撰写 2 条优质英文示例（共 70 条），选中模板时自动展示，点击即填入 textarea
- **版本号展示（P2）**：网站底部新增版本信息 `v4.1.0 · 35 templates`

### Added — 版本管理
- 补齐 Skill 配置文件纳入 Git 追踪（`skill/` 目录）
  - `SKILL.md` — Skill 主配置文件
  - `templates/` — 33 套海报风格 Prompt 骨架模板（01-33）
  - `shared/` — 公共规范文件（bottom-spec / checklist / color-system / company-config）
  - `examples/` — 示例画廊与参考图（gallery.md / paperlight-reference.png）
- 新增 `CHANGELOG.md` 结构化更新日志
- 补打历史 Tag（v1.0.0 – v4.1.0，共 10 个）

### Changed
- `renderVisualExamples()` 在 `selectStyle()` 中联动调用，选中模板即展示示例
- `generateVisualDesc()` 拼接结果写入 textarea 作为唯一数据源，用户可自由编辑

### Tag
- `v4.1.0` → `cf909de` — 主视觉描述体验重构 + 版本管理体系建设

---

## [v4.0.0] - 2026-08-08

### Added
- 新增模板 32 — 校园小报风格（Campus Newsletter）
- 新增模板 33 — DOS 字符画复古风格（DOS ASCII Retro）

### Tag
- `v4.0.0` → `f1bd437` — 新增校园小报 + DOS 字符画模板（templates 32-33）

---

## [v3.2.0] - 2026-08-08

### Added
- 将新丑风模板 31 接入 Prompt Generator 网站（分类筛选 + 标签矩阵 + 风格卡片）

### Tag
- `v3.2.0` → `fc7e08f` — 网站更新新丑风模板

---

## [v3.1.0] - 2026-08-08

### Added
- 新增模板 31 — 新丑风风格（New Ugly / 新丑风）Prompt 骨架

### Tag
- `v3.1.0` → `1c049e3` — 新增新丑风模板（template 31）

---

## [v3.0.0] - 2026-08-06

### Added
- 新增模板 30 — ZINE 极简风格（ZINE minimalist style）

### Tag
- `v3.0.0` → `e2f1137` — 新增 ZINE 极简风格模板（template 30）

---

## [v2.2.0] - 2026-08-01

### Changed
- 更新公司信息为 Star Ring Aerospace Technology Group（`f21c3fa`）
- 移除随机公司生成逻辑，改用固定默认值（`854ecd8`）
- 移除公司英文名中的缩写（缩写：SRATG）（`6e74ae8`）

### Tag
- `v2.2.0` → `f21c3fa` — 企业信息更新为星环航天

---

## [v2.1.0] - 2026-08-01

### Fixed
- 修复 iPad 下拉菜单显示问题
- 新增日历日期选择器

### Changed
- 更新 Prompt Generator：接入 21 个新模板（09-29）+ 分类/标签筛选 UI + 风格标签矩阵（`e68fc9b`）

### Tag
- `v2.1.0` → `548d1c9` — 修复 iPad 下拉显示 + 新增日历日期选择器

---

## [v2.0.0] - 2026-08-01

### Added
- 新增 21 套 Prompt 骨架（templates 09-29）：
  vintage / cyberpunk / morandi / minimal / memphis / forest / popart /
  ukiyo-e / wabisabi / republic / newguofeng / guochao / vaporwave /
  baroque / rococo / handdrawn / filmgrain / blackgold / techbiz /
  warmgold / graybiz

### Changed
- 重命名为 index.html 以适配 GitHub Pages（`ce898a7`）
- 用随机生成器替换硬编码公司信息（`674c89e`）

### Tag
- `v2.0.0` → `e00a731` — 新增大量模板：21 个 Prompt 骨架（09-29）

---

## [v1.1.0] - 2026-08-01

### Added
- 新增交互式 Prompt Generator 网页应用

### Tag
- `v1.1.0` → `8e4fcbb` — 新增 Prompt Generator 交互式网站

---

## [v1.0.0] - 2026-07-31

### Added
- 初始版本：8 套英文 Prompt 骨架（GenerateImage 海报设计系统）
  - 涵盖 album / geometric / warmretro / lightshadow / silent / tech / inkwash / paperlight

### Tag
- `v1.0.0` → `5f9dfe2` — 初始版本：8 个英文 Prompt 骨架

---

## 版本与 Tag 对照表

| 版本    | 提交哈希   | 日期         | 说明                                        |
| ------- | ---------- | ------------ | ------------------------------------------- |
| v1.0.0  | `5f9dfe2`  | 2026-07-31   | 初始版本：8 个英文 Prompt 骨架              |
| v1.1.0  | `8e4fcbb`  | 2026-08-01   | 新增 Prompt Generator 交互式网站            |
| v2.0.0  | `e00a731`  | 2026-08-01   | 新增大量模板：21 个 Prompt 骨架（09-29）    |
| v2.1.0  | `548d1c9`  | 2026-08-01   | 修复 iPad 下拉显示 + 新增日历日期选择器     |
| v2.2.0  | `f21c3fa`  | 2026-08-01   | 企业信息更新为星环航天                      |
| v3.0.0  | `e2f1137`  | 2026-08-06   | 新增 ZINE 极简风格模板（template 30）       |
| v3.1.0  | `1c049e3`  | 2026-08-08   | 新增新丑风模板（template 31）               |
| v3.2.0  | `fc7e08f`  | 2026-08-08   | 网站更新新丑风模板                          |
| v4.0.0  | `f1bd437`  | 2026-08-08   | 新增校园小报 + DOS 字符画模板（32-33）      |
| v4.1.0  | `cf909de`  | 2026-08-09   | 主视觉描述体验重构 + 版本管理体系建设       |
| v4.2.0  | `1407c7a` | 2026-08-15   | AI 即兴创作 + 副标题隐藏开关 + 壁纸模式     |
