---
title: 4D生成模型
summary: 基于分数蒸馏采样思想从video diffusion model中重建可动画的3D模型。
tags:
  - 多模态大模型
  - 分数蒸馏采样
date: 2025-03-01
share: false
# external_link: http://github.com
---
🌟：架构创新；👓：任务创新；🔥：大模型训练。

🌟ICML 2023 MAV3D：第一个基于蒸馏的4D生成，NeRF + Hexplane，T2I+T2V，SDS-T

CVPR2024-4d-fy：在MAV3D的基础上加了3DT2I。3D T2I负责静态几何结构，通用T2I负责refine外观，T2V负责motion；

CVPR2024-A_Unified：在MAV3D的基础上加了3DT2I。

24.2-Animate124：4D grid替换HexPlane；增加3DT2I；refine阶段：用ControlNet SDS对渲染的每一帧图像进行编辑。

🌟ICLR2024-Consistent4D：video-2-4D，直接拟合4D，提出级联多分辨率级联K-planes，用预训练视频插值模型增强时空一致性，pix2pix训练GAN加入cross-frame attention增强帧间一致性。没和MAV3D比。SDS用了3D-T2I，没有用T2V。

CVPR2024-Align_Your_Gaussians：用3DGS替换NeRF，T2I，3D-T2I，T2V。与大家常用的CFG不同，本文用了VSD的思想。以及一些各种正则3DGS的Loss。

23.12-DreamGaussian4D：video-2-4D，用3DGS替换NeRF；静态3DGS+动态deformation field；提取每帧的mesh，优化每帧的texture map。SDS用的3D-T2I。

24.12-4DGen：video-2-4D，3DGS+HexPlane，3DT2I为video frame生成multi view 伪GT来显式地正则4D优化。SDS是3DT2I，没有用T2V。

👓ECCV2024-TC4D：提出volume BBX 刚体运动，并提出基于每小段的轨迹BBX优化。实现全局motion的4D Gen，基于Nerf，采用4Dgrid。

🌟ECCV 2024-STAG4D：video-2-4D。SDS用3DT2I，采用连续帧的时间、空间的KV blend，在attention层次增强一致性。

🌟ECCV2024-SC4D：video-2-4D。稀疏控制点+LBS来表示motion或变形。3DT2I-SDS

🌟24.7-Efficient4D：video-2-4D。基本算是SDS-Free，先生成multi-view video，再重建。时间一致性上，提出volume插值；空间一致性上，采用shared noise predictor。用很小的SDS做refine。

🔥NIPS2024-Diffusion4d：4D-Aware Video Diffusion Model。

🔥NeurIPS-2024-l4gm：4D大重建模型。

🌟NeurIPS-2024-dreammesh4d：video-2-4D。采用MeshGS，control points +LBS驱动。

NeurIPS-2024-4real：只采用T2V，工程化地生成freezing-time video来重建canonical 3DGS。SDS-T优化deformation field。

👓NIPS2024-DreamScene4D：唯一的真实世界video-2-4D。组合式场景优化：静态背景、动态物体，单独重建，后面再基于depth组合。motion分解：表示为物体本身的变形, 物体到世界坐标系的运动, 相机运动。

🌟ICLR2025-EG4D：首个SDS-Free，生成+重建。SVD先生成video，SV3D生成每帧的multiview images得到multiview video，KV blending增强时序一致性。其他许多refine trick：额外颜色线性变换、低质量图像降采样、T2I在图像层面refine。

🌟ICLR2025-MVTokenFlow：SDS-Free。生成+重建。用2D optical Flow在帧间传播，改善生成视频的时间一致性。

🔥ICLR2025-SV4D：video-2-multiview video diffusion model。

👓ICLR2025-AvatarGO：人-物交互子任务。组合式对齐、同步运动。

🌟25.1-AR4D: video-2-4D。自回归式的deformation field：帧间deformation field+全局deformation field。

🔥25.03-WideRange4D：4DVAE。制作一个大范围运动、多场景的4D数据集。静态3D重建，再渐进式拟合4D deformation field。