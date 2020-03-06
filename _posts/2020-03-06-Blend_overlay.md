---
layout: post
categories:
  - UE4
tags: UE4
---

<h1>
    UE4中Blend_Overlay
</h1>

官方文档中

**Blend_Overlay** will either screen or multiply the Base and Blend together. The function does a comparison on the Blend color such that wherever the Blend is brighter than 50% gray, the Base and Blend will be combined via a Screen operation. If the Blend is darker than 50% gray, the Base will be multiplied by the Blend as in the Multiply function.

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/3-6-2020-Overlay.jpg" >

| Item                | Description                                                  |
| :------------------ | :----------------------------------------------------------- |
| Inputs              |                                                              |
| **Base (Vector3)**  | The base, or original texture that will be blended with the Blend texture in some way. |
| **Blend (Vector3)** | The blend texture, which is combined with the base in some way based on the type of blend operation taking place. |

Blend_Overlay将屏蔽或将“基本”和“混合”相乘。 该功能对“混合”颜色进行比较，这样，只要“混合”比50％的灰度亮，就可以通过“屏幕”操作将“基础”和“混合”组合在一起。 如果“混合”比50％的灰度暗，则将“底数”乘以“混合”，如“乘”功能中一样。

简单的说就是亮的像素更亮，暗的像素更暗

