# 变更记录

## v0.1.0 — 2026-11-23

首个公开版本，MIT 许可（可商用，保留版权声明）。

**Skill 本体**
- `SKILL.md` 五个入口：A 拆解 / B 领域 / A′ 立册 / C 设计 / 查词
- `references/` 六份：teardown · booklet · words · intent · survey · sources
- `scripts/` 六个：check_struct · check_js · check_style · check_overflow · check_privacy · run_all
- 新增 `scripts/deny-sample.txt`，让 `--deny-file` 在干净机器上有文件可传

**册子**
- `booklets/03-版式与组件词汇册.html`（起步骨架，3 节，验收用 `--section 3`）
- `booklets/12-路径与轨道词汇册.html`（十节全规格，默认 `--section 10`）

**品牌资产**
- `assets/logo.svg` / `logo-dark.svg`：轨迹 + 停点（继承册子 favicon 的母题）
- `assets/logo-cartoon.svg`：圆头曲线 + 带高光的墨球，用于浅色场景
- `assets/favicon.svg`：100×100 方版
- `screenshots/header.jpg`：README 头图（米白底，右侧是第 12 册真实首屏）
- `screenshots/booklet-12.jpg`：第 12 册首屏实景
- 配色：纸 `#EFF0EC` / 墨 `#15181A` / 砖红 `#B23A2A`；暗场 `#12141A` / `#CE7264`。纪律：砖红在同一个画面里只出现一处

**已知限制**
- 只随仓库分发 2 册；其余 14 册留在作者本地册库
- 溢出检查依赖 `playwright`，缺依赖时打印 `SKIP` 并返回退出码 3（SKIP 不算通过）
