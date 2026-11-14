---
name: bess-electrical-audit
description: Audit SANY BESS device ownership, MW/MWh ratings, DC/AC and MV/LV topology, PV and EMS energy-flow behavior.
---

# bess-electrical-audit

## Target project

本技能用于已有、已获授权的 SANY BESS 模拟器工程。下列文件路径和 npm 命令均相对于目标工程根目录，不是本 Skills 下载包。先确认文件/命令实际存在；缺失时报告未验证，不创建虚假测试结果。本包不包含模拟器源码、内部文档或资产。

## Use

参数、电气归属、能量功率或充放电能流检查。

## Do not use

背景树木材质或界面排版。

## Steps

1. 读取 电气边界（目标工程路径：`docs/electrical/README.md`）、产品登记（目标工程路径：`src/sku/registry.ts`）、资料缺口（目标工程路径：`docs/productization/MISSING_INFORMATION_REGISTER.md`）。厂家资料待确认与演示假设不可混用。
2. 沿 电气生成（目标工程路径：`src/generator/electrical.ts`）、园区网络（目标工程路径：`src/generator/park-network.ts`）、运行拓扑（目标工程路径：`src/topology.ts`） 逐条核对支路、unit/macro归属。1:2/1:4 DC不跨组。
3. A集成柜接AC400V，不重复外置PCS。B电池DC→PCS AC800V→BESS升压变压器→MV/PCC→Factory供电变压器→LV400V；AC800V不得直连AC400V。保持双层母线。
4. PV DC→逆变器→LV；Grid/PCC从MV接入。BMS管理电池，EMS紫色通信不传输功率。整套PCS总功率不能乘面板柜位数。
5. 从有效设备计算MW/MWh，区分额定能量、SOC与瞬时功率。原预设A1.044MWh/0.5MW，B160.512MWh/20MW。核查state/flows的反向、Day充电、Night放电和PV=0。
6. 运行 node --experimental-strip-types tests/topology.test.ts、tests/sku.test.ts、tests/energy-combinations.test.ts；状态改动还跑 node tests/day-night.mjs 并检查EMS/箭头。报告实际端点、量纲和假设，不能声称工程合规。

## Scenarios

- 应触发：怀疑B站能量与功率不同步，核对当前设备求和和拓扑。
- 不应触发：修改沿海岩石粗糙度。
