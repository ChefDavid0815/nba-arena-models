# Unreal import / Unreal 导入

**Validated with Unreal Engine 5.8.2 on 2026-09-20. / 2026-09-20 使用 Unreal Engine 5.8.2 验证。**

The validation is an actual import into an isolated blank project, not just a filename check. It does not prove game performance, collision, animation quality or final material parity.

验证为隔离空白工程中的实际导入，并非仅检查扩展名；不代表游戏性能、碰撞、动画品质或最终材质效果已验证。

## Blender source / 原生 Blender

Open `Blender/ChaseCenter_CP80.blend` in Blender 5.2.2 or later. Use scene `ChaseCenter_RealismPolish_v03` for the interior, or `ChaseCenter_Exterior_Day_v04` for the exterior. Modeling textures are packed. The reference guides and text scripts were removed from the publication copy.

使用 Blender 5.2.2 或更高版本打开原生文件。内景选择 `ChaseCenter_RealismPolish_v03`，外景选择 `ChaseCenter_Exterior_Day_v04`。必要贴图已打包，发布副本移除了参考辅助集合与脚本文本。

## FBX for Unreal / FBX 导入

1. Extract the package before importing. 解压后导入。
2. Import `FBX/ChaseCenter_Cutaway.fbx` or `FBX/ChaseCenter_Exterior.fbx` as **Static Mesh**, with **Combine Meshes** enabled. 分别作为静态网格导入，开启合并网格。
3. Keep scale at 1 initially and verify the court’s 28.6512 × 15.24 m dimensions. Native Blender units are metres; Unreal uses centimetres. 保持导入缩放为 1，再以标准球场尺寸检查单位。
4. FBX preserves geometry and portable materials, with embedded required image maps. Procedural Blender shaders require baking or rebuilding for parity. FBX 保留几何及简化材质，必要图片贴图已嵌入；程序材质需烘焙或在引擎中重建。
5. Configure collision, LOD/Nanite, lighting and scene partitions for your game. 按实际游戏工程配置碰撞、LOD/Nanite、灯光及场景拆分。

The FBX cutaway is deliberately roof-open. It does not include the full native Geometry Nodes seating setup. Full seats, interior and exterior remain in the `.blend`; chair count is 13,332 instances, not an official capacity claim. The compressed `Preview/*.glb` files are browser presentation copies using Draco, not the recommended Unreal import path.

内景 FBX 为揭开屋顶的展示版，不包含完整 Geometry Nodes 座椅系统。完整座椅、内外景保留在 `.blend` 中；13,332 是实例数，不是官方座位容量。压缩 GLB 是使用 Draco 的网页预览副本，Unreal 建议走 FBX 导入。

## Verification boundary / 验证范围

- Interior FBX → `StaticMesh`: passed. 内景静态网格导入通过。
- Exterior FBX → `StaticMesh`: passed. 外景静态网格导入通过。
- Visual parity, collision, playable scenes and frame-rate budgets: not established. 最终视觉一致性、碰撞、可玩关卡与帧率预算尚未验证。
