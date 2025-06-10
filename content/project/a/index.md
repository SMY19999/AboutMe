---
title: 3D生成大模型
summary: 尝试将AR架构用于mesh densification任务。
tags:
  - 多模态大模型
date: 2025-03-01
share: false
# external_link: http://github.com
---
广泛调研了2025年3月之前的3D生成大模型的研究，思考两种主要生成范式（自回归AR、大重建模型LRM）与3D表示的关系，[相关材料](3D生成调研与思考.pdf)。

一个简短的结论：
- 由于AR架构是face-by-face生成，适合对拓扑要求较高的场景（可动画的角色、锋利特征）；其难点在于mesh的tokenization。
- LRM架构从3D特征中解码出3D表示，适合静态物体；对于mesh而言，一般需要做重拓扑以适配LOD的需求；其难点在于如何将mesh高效地压缩到特征空间中。

**问题描述**：由于当前3D生成大模型最主要的落地场景还是游戏，本人调研了游戏美术开发的需求，发现网格重拓扑是一项非常耗时的任务。
基于重拓扑算法的mesh simplification或remesh能够在一定程度上加快开发进程，但mesh densification是当前的图形学手段无法解决的问题。
举例来说，一个100k面的网格变为1k是可以实现的，但反过来是无法实现的。

**研究动机**：
本人对AR架构比较感兴趣，由于是face-by-face生成，自然地想到可以用AR架构来做mesh densification任务。
一个理想的功能：输入低模，随后AR模型逐步向低模插入face，最终得到高模，整个过程可以随时停止。

**方案探索**：
本人曾尝试提出一种基于网格重拓扑的mesh tokenization方案，待详细说明。