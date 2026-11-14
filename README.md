# SANY BESS Agent Skills

公开的五个 Agent Skills 工作流，V10.3 发布快照。此仓库仅提供技能说明，不包含储能模拟器应用源码、内部技术文档、照片、模型、日志或用户方案。完整模拟器工程继续独立管理。

## 下载

- [下载 ZIP](https://github.com/dk22246/sany-bess-agent-skills/archive/refs/heads/main.zip)
- 克隆：`git clone https://github.com/dk22246/sany-bess-agent-skills.git`

## 技能

- [project-onboarding](skills/project-onboarding/SKILL.md)
- [bess-electrical-audit](skills/bess-electrical-audit/SKILL.md)
- [layout-ga-validation](skills/layout-ga-validation/SKILL.md)
- [environment-blender](skills/environment-blender/SKILL.md)
- [regression-handoff](skills/regression-handoff/SKILL.md)

## 使用

1. 解压后，将所需的 `skills/<name>` 目录放入目标工程的 `.agents/skills/`，保留 `SKILL.md` 文件结构。已有同名技能时先比较差异。
2. 在 Agent 中明确要求使用该技能，或让 Agent 读取对应 SKILL.md。自动发现路径取决于使用的 Agent 及其版本。
3. 技能内的源码/文档路径和 npm 命令属于目标模拟器工程。需要已有工程的访问权限；本下载包不能单独运行3D模拟器。缺失依赖、文件或命令时应报告，不得假装检查通过。

当前 Codex 项目级发现采用 `.agents/skills/`。其他 Agent 可先手动读取 SKILL.md；未完成独立跨 Agent 运行认证。

`manifest.json` 记录每个技能的来源文本摘要和公开文本摘要。公开版将私有工程相对链接转换为目标工程路径说明；未复制其内部文档。
