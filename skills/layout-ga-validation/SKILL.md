---
name: layout-ga-validation
description: Validate generated layouts, shell clearances, independent unit routes and actual-world GA dimensions and exports without changing protected plans.
---

# layout-ga-validation

## Target project

本技能用于已有、已获授权的 SANY BESS 模拟器工程。下列文件路径和 npm 命令均相对于目标工程根目录，不是本 Skills 下载包。先确认文件/命令实际存在；缺失时报告未验证，不创建虚假测试结果。本包不包含模拟器源码、内部文档或资产。

## Use

Auto Layout、GeneratedPlan、净距、GA和布线校验。

## Do not use

仅改环境美术或文档错字。

## Steps

1. 读 布局入口（目标工程路径：`docs/generator/README.md`），再查engine/auto-solver/auto-types及plan geometry/data/drawing/view和调用者。不要重写Solver。
2. 比较设备ID、坐标旋转、unit/macro、外壳/基础、围栏维护带及DC/MV路由；净距、中心距、基础距、模块包络与电缆长分别记录。
3. 按真实外缘测量minimum/exact。4022.5mm不得写成4000mm。验证固定场地、0/90旋转、确定候选和失败保留旧方案。
4. 保护 Frozen Plan（目标工程路径：`src/sku/frozen-v93.json`） 和 模型/GA基线（目标工程路径：`tests/fixtures/pre-sku-models-ga.json`）。原预设32电池/8PCS/4Macro，其他配置依输入。不得改Golden掩盖失败。
5. npm run test:auto-layout；node --experimental-strip-types tests/plan.test.ts；node --experimental-strip-types tests/generator.test.ts；npm run reproduce。交互变动跑 auto-layout-browser、generator-browser、plan-browser。
6. 真实浏览器检查世界壳体投影、总图/典型详图、尺寸图层、SVG/2400/4800 PNG和1280可读性。数据一致与画面可读分别报告。

## Scenarios

- 应触发：补电池到PCS净距尺寸，计算几何并检查导出。
- 不应触发：修改夜间路灯颜色。
