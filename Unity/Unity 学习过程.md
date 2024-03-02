---
title: Unity 学习过程
category: /小书匠/日记/2024-03
grammar_cjkRuby: true
---

参考视频：[Unity教程 零基础带你从入门到大神](https://www.bilibili.com/video/BV1gQ4y1e7SS?p=7&spm_id_from=pageDriver&vd_source=d1002d9c1ba92da4ba3fca4fdca6d750)

06 视频中提到

Unity遵守 左手坐标定律，则：

![](./images/1709396475408.png)

每个方块都遵守的，就叫做**世界坐标系**

而一旦方块成为了某方块的**子方块**
![](./images/1709396535949.png)
Quad 为父物体
Plane 为子物体

那么子方块的坐标 并非遵守 世界坐标系。而是 **父物体**自己的坐标系，则是 **本地坐标系**

**For Example：**
移动前：
这是Quad的坐标
![](./images/1709396755859.png)
这是Plane的坐标
![](./images/1709396767603.png)

移动后：
Quad：
![](./images/1709396804633.png)
Plane：
![](./images/1709396833047.png)

所以 父物体 怎么移动 子物体 的坐标都不变。

显示中，有轴心(Pivot)和中心(Center)区分，不影响操作。
位于左上角的：
![](./images/1709396937640.png)