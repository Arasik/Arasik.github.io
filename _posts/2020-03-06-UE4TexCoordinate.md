---
layout: post
categories:
  - UE4
tags: UE4
---

<h1>
    UE4中TextureCoordinate
</h1>

官方文档中

The **TextureCoordinate** expression outputs UV texture coordinates in the form of a two-channel vector value allowing materials to use different UV channels, specify tiling, and otherwise operate on the UVs of a mesh.

| Item                 | Description                                                  |
| :------------------- | :----------------------------------------------------------- |
| Properties           |                                                              |
| **Coordinate Index** | Specifies the UV channel to use.指定要使用的紫外线通道。     |
| **UTiling**          | Specifies the amount of tiling in the U direction.指定U方向的平铺量。 |
| **VTiling**          | Specifies the amount of tiling in the V direction.指定V方向的平铺量。 |
| **Un Mirror U**      | If *true*, undo any mirroring in the U direction.如果是true，撤消U方向的任何镜像。 |
| **Un Mirror V**      | If *true*, undo any mirroring in the V direction.如果是true，撤消在V方向的任何镜像。 |

简单的说就是 u是几 那么在u方向就重复几次，v是几就在v方向重复几次