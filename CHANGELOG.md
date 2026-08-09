# Changelog

本项目所有重要变更均记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

---

## [Unreleased]

### Added
- 补齐 Skill 配置文件纳入 Git 追踪（`skill/` 目录）
  - `SKILL.md` — Skill 主配置文件
  - `templates/` — 33 套海报风格 Prompt 骨架模板（01-33）
  - `shared/` — 公共规范文件（bottom-spec / checklist / color-system / company-config）
  - `examples/` — 示例画廊与参考图（gallery.md / paperlight-reference.png）

---

## [v4.0.0] - 2026-08-08

### Added
- 新增模板 32 — 校园小报风格（Campus Newsletter）
- 新增模板 33 — DOS 字符画复古风格（DOS ASCII Retro）
- 将新丑风模板 31 接入 Prompt Generator 网站（`fc7e08f`）

### Tag
- `v4.0.0` → `f1bd437` — 新增校园小报 + DOS 字符画模板（templates 32-33）

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

### Changed
- 更新公司信息为 Star Ring Aerospace Technology Group（`f21c3fa`）
- 移除随机公司生成逻辑，改用固定默认值（`854ecd8`）
- 移除公司英文名中的缩写（缩写：SRATG）（`6e74ae8`）

### Tag
- `v3.0.0` → `e2f1137` — 新增 ZINE 极简风格模板（template 30）

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

| 版本    | 提交哈希   | 日期         | 说明                                    |
| ------- | ---------- | ------------ | --------------------------------------- |
| v1.0.0  | `5f9dfe2`  | 2026-07-31   | 初始版本：8 个英文 Prompt 骨架          |
| v1.1.0  | `8e4fcbb`  | 2026-08-01   | 新增 Prompt Generator 交互式网站        |
| v2.0.0  | `e00a731`  | 2026-08-01   | 新增大量模板：21 个 Prompt 骨架（09-29）|
| v2.1.0  | `548d1c9`  | 2026-08-01   | 修复 iPad 下拉显示 + 新增日历日期选择器 |
| v3.0.0  | `e2f1137`  | 2026-08-06   | 新增 ZINE 极简风格模板（template 30）   |
| v3.1.0  | `1c049e3`  | 2026-08-08   | 新增新丑风模板（template 31）           |
| v4.0.0  | `f1bd437`  | 2026-08-08   | 新增校园小报 + DOS 字符画模板（32-33）  |
