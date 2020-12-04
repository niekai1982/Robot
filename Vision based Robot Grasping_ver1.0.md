# Vision based Robot Grasping

------
> Sun Lei, Zhao Xue, Nie Kai

[toc]

## Abstract

## 1. Robotic Grasp

![image-20201118093331296](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9g9maej30mj0dq3zn.jpg)

> **Grasp what we do is just where should the robot put the gripper or suction cup with what orientation.**

## 2. Key words

- **Grasp Configuration**

  The position and orientation of the arm to the object[^21].

- **Grasp planning**

  Grasp planning considers the problem of finding grasps for a given object that achieve force closure or optimize a related quality metric [^2], and typically assume that grasped object and contact location are known exatactly

- **Grasp Sampling**

  Cross-Entropy Method(CEM) is a simple derivative-free optimization algorithm that samples a batch of N values at each iteration, fits a Gaussian distribution to M < N of these samples, and then samples a new batch ofN from this Gaussian. 

- **Robust Grasp Planning** (RGP)  
  
  **Maximize grasp robustness**, or the expected value of an analytic metric under uncertainty in sensing and control. In another world, RGP consider the same problem as grasp planning in the presence of bounded pertubations in properties such as friction, which are inevitable due to imprecision in perception and control[^4].

- **Grasp detection**

  Grasp detection which aimed to get grasp configuration is analogous to object detection in computer vision with the only difference being added term for the gripper orientation[^6].

- **Grasp Synthesis Algorithm**

  During a grasping task execution, the grasping fingers must be controlled so that the grasp processes dexterity, equilibrium, stability and dynamic behavior. Such a control scheme, requires methods of computing the finger parameters (po-sitions and forces of fingertips and joints). **These algorithms are referred to as robotic grasp synthesis algorithms.** 

- **Force Closure**

  Consider a single movable body and a number of frictional contacts. We say the contacts result in **force closure** if the **composite wrench cone** contains the entire wrench space, so that any external wrench Fext on the body can be balanced by contact forces.Sample requires that the grasp of the object can **resist any possible direction of force/torque perturbation** to the objcet.
  
- **Form Closure**

  Form closure is defined as a condition of complete restraint in which the grasped body can resist any external disturbance wrench, **irrespective of the magnitude of the contact force**.Form closure is a **stronger condition than force closure**. More formally, a grasp is defined as form closed if and only if it is force closed with frictionless contacts [^1].

- **Probability of Force Closure** $P_f$

  $P_f$ was denoted to estimate the probability of attaining a force closure grasp for a large set of grasps and objects[^5].

- **Perturbation**

  Perturbation in properties such as object shape, pose or mechanical properties such as friction. One way to treat perturbations: statistical sampling, explore how a robust grasp computed from one object can guide the search for robust grasps on similar objects

  - Recent **research** has studied labelling grasps in database with metrics that are robust to imprecision in perception and control **using probability of force closure** or expected Ferrari-Canny quality
  - Another line of **research** has focused on **synthesizing grasps** using statistic models learned from database of images or point clouds of objects **annotated with grasps from human demonstrators or physical execution**
  
- **3-DOF Grasps**

  3-DOF grasps respresents the grasp as an oriented rectangle in the image which constrains the gripper pose to be parallel to the image plane.

- **6-DOF Grasps**

  Predict the full 6-DOF pregrasp pose



## 3. Categorization of Methods

### 3.1 Analytic Methods

Analysic(or sometime called geometric) approachs typically annalyze the shape of a target object and consider kinematics and dynamics formulation  to determine a suitable grasps. There is a wide disparity in the terminology used in the grasping literature regarding equilibrium, stability, force closure and form closure terms.

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9i1d3xj30mr0iljtu.jpg" alt="image-20201118093630187" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9mqhcyj313e0oojuj.jpg" alt="image-20201118100113704" style="zoom: 50%;" />



Alongside with models for

- Contact forces
- Kinematic constraints(no penetration).
- Interaction principles(friction law, restitution law, maximal dissipation, ...)

However

- Leads to complex modeling and computational issues under actuation, hybdidness, weakly observability, noise,...

Hence

- The story of the mechanics of robotic grasp is one of finding sumplifications

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9ddfhdj30r60be3zf.jpg" alt="image-20201118102436557" style="zoom:33%;" />

[^11]:Mobility of Bodies in Contact—Part I: A 2nd-Order Mobility Index for Multiple-Finger Grasps 

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9lczt1j314i0sajvb.jpg" alt="image-20201118103755107" style="zoom: 33%;" />

[^12]:GraspIt!: A Versatile Simulator for Robotic Grasping Andrew T. Miller 

### 3.2 Empirical (Data Driven) Methods

Typically use machine learning to develop models that map from robotic sensor readings directly to success labels from labels from humans or physical trails[?]. Furthermore, approaches can be categorized as model-based or model-free, depending on wether or not specific knownledge about object is used to solve the consider task[^6].



![image-20201120095211427](https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei6z7ttj317g0u07ed.jpg)

#### 3.2.1 Model-Based

Model-based approaches for known rigid objects typically include a pose estimation step and allow a precise placement of the objects. Model-based robotic grasping can be consider as a three-stage process:

- Object pose estimation

- Grasp pose determination ~~ (grasp plan??)~~

- Plan collision-free and kinematically feasible path

###### 3.2.1.1  ==Object pose estimation==

![image-20201119105718512](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9hsbqhj31lk0u0k8k.jpg)

- Problem of Occlusion and symmetry

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum990q96j31hk0tuwpe.jpg" alt="image-20201119164244932" style="zoom:70%;" />

- Problem of collecting labeled data

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9dzuqtj314t0kftet.jpg" alt="image-20201119164346246" style="zoom:67%;" />

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9jmi5dj31400fwdke.jpg" alt="image-20201119164418488" style="zoom:67%;" />

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9kf33uj30wb0jzwir.jpg" alt="image-20201119164512112" style="zoom:80%;" />

- Problem of efficient

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9k1u5ij310c0jugru.jpg" alt="image-20201119164830326" style="zoom: 67%;" />

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9kvxsxj31430fv42x.jpg" alt="image-20201119164927829" style="zoom:67%;" />

###### 3.2.1.2 Grasp pose determination (grasp plan??)

###### ![image-20201118145418206](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9gyouoj31io0u0112.jpg)3.2.1.3 Plan collision-free and kinematically feasible path

![image-20201118145436644](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9mbw5hj31ji0rwn1j.jpg)

#### 3.2.2 Model-Free

Model-free approaches are attractive due to their ablility to generalize to unseen objects and pose a dominant direction in robotic grasping research. They do not use prior knowledge about the objects and therefore **work without a pose estimation step**. Model-free approaches ==directly propose grasp candidates== and typically aim for generalization to novel objects.

##### 3.2.2.1 Supervised Learning

Supervised learning is concerned with learning a mapping based on labeled training data, and can be categorized as discriminative or generative depending on whether the grasp configuration is the input or output.

###### A. Discriminative Model

Discriminative approaches **sample grasp candidates and rank them using a nerual network**, the robot chooses the grasp with the highest score.

- GraspNet[^13]

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9ad87sj31jo0t412a.jpg" alt="image-20201118205550485" style="zoom:80%;" />

[^13]:Mousavian A, Eppner C, Fox D. 6-DOF GraspNet: variational grasp generation for object manipulation. In: IEEE, editor. IEEE International Conference on Computer Vision (ICCV); October 27 – November 2, 2019; Seoul, Korea; 2019. Addresses model- free grasping in 6D.

- Hand-eye coordination for robotic grasping

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum98u8dmj31hk0tuwpe.jpg" alt="image-20201118205711312" style="zoom:80%;" />

- Dex-Net

![image-20201119160959244](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9oc3qqj31d40u0k71.jpg)

![image-20201119163255373](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9itfkbj31h70u0tpp.jpg)

###### B. Generative Model

Generative approach output a grasp configuration. One approach to this--called robotic grasp detection--is to detect oriented rectangles in the image plane, which represent promising grasp candidates for parallel jaw grippers. This parameterization comprises the position, orientation, and opening width of the gripper.

- Robotic Pick-and-Place of Novel Objects in Clutter with Multi-Affordance Grasping and Cross-Domain Image Matching[^15]

![image-20201119104843942](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9bbnf6j31ln0u0nca.jpg)

![image-20201119104843942](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9bbnf6j31ln0u0nca.jpg)



## 4. Datasets

### 4.1 Pose Estimation

- GraspNet dataset, https://graspnet.net/index.html

  ![img](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9nn0u9j30dc07iaaz.jpg)



- HomebrewedDB, http://campar.in.tum.de/personal/ilic/homebreweddb/index.html

![image-20201119143059363](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum99mtw3j30n40b8770.jpg)

- YCB-Video,https://rse-lab.cs.washington.edu/projects/posecnn/

![image-20201119143146538](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9n8uzcj30n4056aaq.jpg)

- T-LESS, http://cmp.felk.cvut.cz/t-less/

![image-20201119143236480](https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9cvlibj30n40dy418.jpg)

- BOP: Benchmark for 6D Object Pose Estimation, https://bop.felk.cvut.cz/home/

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9ehi49j31ab0u0gxl.jpg" alt="image-20201119143355218" style="zoom:50%;" />

### 4.2 Grasp

- Fraunhofer IPA Bin-Picking dataset 

https://www.bin-picking.ai/en/dataset.html

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9fbi0lj30n40bkn02.jpg" alt="image-20201119144210047" style="zoom:67%;" /> 

- Siléane Dataset for Object Detection and Pose Estimation, http://rbregier.github.io/dataset2017

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9lxqjej30n409idhh.jpg" alt="image-20201119143607987" style="zoom:67%;" />

- Dataset of Dex-Net, https://berkeleyautomation.github.io/dex-net/#dexnet_21

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9c1hgaj30n40p4adk.jpg" alt="image-20201119143646934" style="zoom:50%;" />

- Amazon Robotics Challenge dataset(2017), https://vision.princeton.edu/projects/2017/arc/

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9ciuvlj30n406cjt2.jpg" alt="image-20201119143728098" style="zoom:67%;" />

- Cornell grasping dataset, http://pr.cs.cornell.edu/grasping/rectdata/data.php

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9omu4uj30n40ekgn5.jpg" alt="image-20201119143804880" style="zoom:67%;" />

- Jacquard dataset, https://jacquard.liris.cnrs.fr/

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkum9fqanmj30n40fmq5e.jpg" alt="image-20201119143850240" style="zoom:67%;" />

## 5. Challenges

- Environment
  **Obstacle**
- Dense
  **Clutter**
- Object
  **Variability**

## 6. Top Expert Should Be Following



- **Berkeley,  Ken Goldberg, https://berkeleyautomation.github.io/dex-net/#dexnet_4**

  

  <img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei51ywcj30y70u0k62.jpg" alt="image-20201120094325148" style="zoom:50%;" />

  

- **MIT, Alberto Rodrigue, http://mcube.mit.edu/publications.html**

  

  <img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei3t682j31lq0qo46n.jpg" alt="image-20201120093850238" style="zoom:50%;" />

  <img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei5gbtmj30y90u0dum.jpg" alt="image-20201120093927520" style="zoom:50%;" />

  

- **Princeton Vision and Robotics Group, http://3dvision.princeton.edu/research.html**

  

  <img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei3h22qj31lq0qo46n.jpg" alt="image-20201120094509177" style="zoom:50%;" />

- **Google, https://docs.google.com/presentation/d/e/2PACX-1vTZD619SHMJ6yWjo-sO4eJNhWs4HiGDskqwKutim8oqYue5Zfxv-B6MrwGg5Q32eDhRPlfKA77QwBYx/pub?start=false&loop=false&delayms=60000&slide=id.g6adae1ebc3_1_38**

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei62zchj31ha0u0tmq.jpg" alt="image-20201120094728190" style="zoom:50%;" />



- **Stanford,Feifei Li, https://roboturk.stanford.edu/**

  

  <img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei4hwtjj313n0u017z.jpg" alt="image-20201120094109146" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/0081Kckwgy1gkvei7s3erj31880u0dns.jpg" alt="image-20201120094137420" style="zoom:50%;" />

## References

[^1]: Bicchi, A., & Kumar, V. (2000, April). Robotic grasping and contact: A review. In Proceedings 2000 ICRA. Millennium Conference. IEEE International Conference on Robotics and Automation. Symposia Proceedings (Cat. No. 00CH37065) (Vol. 1, pp. 348-353). IEEE.
[^2]: F. T. Pokorny and D. Kragic, “Classical grasp quality evaluation: New theory and algorithms,” in IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2013.
[^3]: Sahbani A, El-Khoury S, Bidaud P. An overview of 3D object grasp synthesis algorithms. In: Robotics and Autonomous Systems; 2012.
[^4]: Jeffrey Mahler, Dex-Net 1.0
[^5]:  J. Weisz and P. K. Allen, “Pose error robust grasping from contact wrench space metrics,” in Robotics and Automation (ICRA), 2012 IEEE International Conference on. IEEE, 2012, pp. 557–562.
[^6]: Kilian Kleeberger, A Survey on learning-Based Robotic Grasping
[^21]: Nima Shafii, Learning to grasp familiar objects using object view recognition and template matching. In 2016 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2016.