---
name: environment-blender
description: Produce and integrate four Blender scenery environments; validate GLB manifests, PBR UV normals LOD provenance guards and day-night GPU evidence.
---

# environment-blender

## Target project

本技能用于已有、已获授权的 SANY BESS 模拟器工程。下列文件路径和 npm 命令均相对于目标工程根目录，不是本 Skills 下载包。先确认文件/命令实际存在；缺失时报告未验证，不创建虚假测试结果。本包不包含模拟器源码、内部文档或资产。

## Use

Blender资产、四环境组织材质、场景性能与昼夜验收。

## Do not use

电气求解或储能产品模型重制。

## Steps

1. 读 可视化入口（目标工程路径：`docs/visualization/README.md`）、流水线（目标工程路径：`assets/environment/scripts/generate.py`）、Manifest（目标工程路径：`public/environment/models/manifest.json`），定位assets/placement/scenery。只有industrial/quarry/tropical/coastal四种。
2. 检查Blender实际版本；未安装明确报告，不能声称建模完成。设置BLENDER_PATH后 npm run build:environments；预构建GLB普通用户不依赖Blender。
3. 核对实际尺寸、轮廓、锚点、UV/法线/坐标轴、LOD、共享PBR与来源许可/hash。Normal/Rough按Non-Color；源下载ignored，优化源/元数据可分发。
4. GLTFLoader共享资源，重复植被实例化；按保护区/碰撞结果放置，不移设备、基础、围栏、维护带或线路迁就美术。切换环境不重建方案或残留对象。
5. 运行 node tests/environment-assets.test.mjs 和环境单元/浏览器专项；检查四组合、12次切换资源趋势和各环境Day/Night，夜间PV=0。
6. 固定A+B+PV、45°仰角/FOV43、viewport/DPR保存八张真实截图；同GPU/驱动/浏览器/规模比FPS、调用、三角形、纹理、几何。不得合成图代替浏览器。用户视觉确认与测试通过分开，树冠等已知限制仍需说明。

## Scenarios

- 应触发：重生成热带树冠并验证LOD和避让。
- 不应触发：审查PCS AC800V接入层级。
