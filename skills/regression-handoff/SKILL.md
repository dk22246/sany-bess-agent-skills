---
name: regression-handoff
description: Execute scoped SANY BESS regression, protect frozen data and private assets, then deliver a traceable handoff distinguishing tested and untested evidence.
---

# regression-handoff

## Target project

本技能用于已有、已获授权的 SANY BESS 模拟器工程。下列文件路径和 npm 命令均相对于目标工程根目录，不是本 Skills 下载包。先确认文件/命令实际存在；缺失时报告未验证，不创建虚假测试结果。本包不包含模拟器源码、内部文档或资产。

## Use

开发后的回归、提交和工程交接。

## Do not use

简单问答或一句翻译。

## Steps

1. 记录初始Git/HEAD/状态、边界、影响模块/调用者/夹具；保留无关修改。读 质量契约（目标工程路径：`docs/quality/REPRODUCIBILITY.md`） 和 兼容矩阵（目标工程路径：`docs/quality/AGENT_COMPATIBILITY.md`）。
2. npm run doctor；npm run verify:portable。分别核对设备、拓扑、布局、GA、Revision和方案hash；不得改Frozen/Golden消除回归。
3. 有健康开发服务和Chromium再 npm run verify:browser。记录真实命令/平台/版本/退出码/失败原因；未获得GPU、Agent或第二台电脑则NOT TESTED。
4. 视觉改动另做固定条件真实截图、昼夜能流、拾取/镜头/GA导出与GPU性能；PASS不能替代画面确认。
5. 只暂存本次明确文件；npm run inventory；npm run check:repository；node scripts/check-release-files.mjs；git diff --cached --check。不得上传私照/日志/用户方案/Token。
6. 更新当前状态/版本索引/CHANGELOG，分清已实现/已测/未测/需批准/计划。授权范围内提交任务分支，核对remote SHA和Private；不强推或自动改默认分支。

## Scenarios

- 应触发：完成布局改动后做受控回归并交接。
- 不应触发：解释MWh缩写。
