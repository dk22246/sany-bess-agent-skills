---
name: project-onboarding
description: Orient a new developer or Agent in this SANY BESS repository, verify the checkout, install and diagnose the local application.
---

# project-onboarding

## Target project

本技能用于已有、已获授权的 SANY BESS 模拟器工程。下列文件路径和 npm 命令均相对于目标工程根目录，不是本 Skills 下载包。先确认文件/命令实际存在；缺失时报告未验证，不创建虚假测试结果。本包不包含模拟器源码、内部文档或资产。

## Use

新Agent接手、首次安装、确认版本和启动入口。

## Do not use

纯翻译或已定位的单行修复。

## Steps

1. 读取 AGENTS（目标工程路径：`AGENTS.md`）、文档入口（目标工程路径：`docs/README.md`）、当前状态（目标工程路径：`docs/releases/PROJECT_STATUS_V10.3.md`）。无法读取本地仓库时明确说明，不根据聊天伪称已核实。
2. 记录 git status --short、git branch --show-current、git rev-parse HEAD、git remote -v；核对默认分支和发布报告，不覆盖其他人的修改。
3. 按 架构（目标工程路径：`docs/architecture/SYSTEM.md`） 和 文件依赖索引（目标工程路径：`docs/architecture/repository-index.json`） 定位 generator/sku/plan/environment 与 main/layout/state/topology。区分实现、计划、历史和假设。
4. 按 Quick Start（目标工程路径：`docs/getting-started/QUICK_START.md`） 使用 npm ci。已有用户服务时先检查健康；干净安装在独立工作区进行，避免打断现有依赖。
5. npm run doctor；npm run start:local；npm run health。固定5173失败先核对HTTP身份、PID归属和生命周期日志，不换端口或杀未知进程。
6. npm run verify:portable 建立修改前基线。记录真实工具版本/平台/退出码/未测项，解释原预设、参数化组合和四环境；普通运行不要求Blender。

## Scenarios

- 应触发：克隆后确认B站配置并启动，执行doctor和reproduce。
- 不应触发：将一个中文按钮翻译为英文。
