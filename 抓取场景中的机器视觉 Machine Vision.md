### 机器视觉 Machine Vision

---

机器视觉的目的是给机器人提供操作物体的信息，物体抓取领域主要研究内容

- Object Recognition
- Pose Estimation
- Camera Calibration



#### Pipline

Calibration -> Pose Estimation -> Motion Plan

https://www.zhihu.com/question/26199861/answer/154228960



#### Calibration

> 求解机器人坐标系和视觉系统坐标系的转换矩阵

https://mp.weixin.qq.com/s?__biz=MzA5MDE2MjQ0OQ==&mid=2652786821&idx=1&sn=297af3939075dbc926e6d785911104e9&chksm=8be524fbbc92aded68bacb1766df0a17127a96f22e1e39199f554b51511a1a9dae4a639810ef#rd

##### eye to hand

> 摄像头安装在手臂之外的部分，与机器人的基座（世界坐标系）相对固定，不随着机械臂的运动而运动；



#### Object recognition



##### 平面物体检测

> 主要计算物体$(x, y, \theta)^{T}$ 三自由度

主要方法为边缘提取+边缘匹配/形状匹配， 为了提高稳定性，一般通过打光源、采用反差大的背景等手段，减少系统变量。



##### 有纹理



环境复杂性：

- 光照条件不确定性
- 物体与相机之间距离不确定性（尺度）
- 成像角度的不确定性（旋转，仿摄）
- 遮挡

经典方法

- SIFT（scale-invariant feature transform）
- SURF
- ORB



##### 无纹理

Template Matching

- LineMod

> Lined 与shape based matching 同宗同源, https://zhuanlan.zhihu.com/p/45538349

##### 深度学习

CNN detection&segmentation



#### Pose Estimation

> 物体完整位姿$(x,y,z,rx,ry,rz)^{T}$



CNN

- Two Stage
  - detetion & segmentation
  - ICP

- END-to-END
  - 2D pose estimation
  - 3D pose estimation

