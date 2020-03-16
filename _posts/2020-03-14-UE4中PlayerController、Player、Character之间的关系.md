---
layout: post
categories:
  - UE4
tags: UE4
---

# ue4中PlayerController、Player、Character之间的关系

Unreal里PlayerController、Player、Character之间的关系，要理解它们之间的关系，本质是搞明白Pawn和Controller的关系。



### Pawn是马甲，Controller是驱动马甲的大脑。
Controller通过possess/unposses来获得/释放对Pawn的控制权。 Controller和Pawn相对独立，不一定谁必须有谁。
Controller有两种：AIController和PlayerController。 前者是人工智能的控制，后者是用户输入控制。
Controller和Possession的关系是1:1。所以一个Controller至多能控制一个Pawn,一个Pawn至多能被一个Controller控制。

回答标题，Character是什么，Player是什么？

Character是Pawn的一种。 
至于Player，没有这个类，只是在Blueprint里有带有player字眼的节点，比如Get Player Character节点和Get Player Pawn节点。
————————————————
版权声明：本文为CSDN博主「whatchacha」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u010153703/article/details/38321765