---
layout: post
catogories:
  - Unreal Engine 4
tags: Unreal Engine 4
---

# UE4中事件ActorBeginOverlap

![3-23-2020-2.png](https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/3-23-2020-2.png)

当指定对象与另一个对象重叠（空间坐标位置的物体重叠）时执行

例如，一名玩家走进扳机。 对于物体发生阻塞性碰撞的事件，例如玩家撞墙，请参阅“击中”事件。 注意：此Actor和另一个Actor上的组件都必须将bGenerateOverlapEvents设置为true才能生成重叠事件。