---
title: 视频生成模型
summary: 物理增强的多物体运动控制的视频生成模型。
tags:
  - 视频生成
date: 2025-03-01
share: false
# external_link: http://github.com
---
构建物理仿真数据集，将力的大小与方向编码为图像，并作为控制条件通过ControlNet注入CogVideoX中。
在仿真数据集中增加静止参考对象、多物体运动仿真数据，可以泛化为基于力的多物体运动控制。
<!-- ![]("生成结果") -->
{{< video src="1.mp4 " controls="yes" >}}
{{< video src="2.mp4 " controls="yes" >}}