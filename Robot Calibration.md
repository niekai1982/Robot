

Kinematices Analysis and Simulation of KUKA Robot



###### KR 210 R2700 extra

![image-20210106143723407](/Users/kainie/Library/Application Support/typora-user-images/image-20210106143723407.png)

![image-20210106144747699](/Users/kainie/Library/Application Support/typora-user-images/image-20210106144747699.png)



![image-20210106144805280](/Users/kainie/Library/Application Support/typora-user-images/image-20210106144805280.png)

![image-20210106143656066](/Users/kainie/Library/Application Support/typora-user-images/image-20210106143656066.png)

![image-20210106143834096](/Users/kainie/Library/Application Support/typora-user-images/image-20210106143834096.png)

#### D-H matrix in Robot 

>  Denavit-Hartenberg parameters



In 1955 Denvit and Hartenberg put forward (D-H) matrix method

Relation between the coordinate frames attached to the end-effector and the base.

position and orientation of the rigid body

![image-20210112100931782](/Users/kainie/Library/Application Support/typora-user-images/image-20210112100931782.png)

$T_5^{0}$ Robot manipulator coordiante system relative to the postion and orientation of the fixed coordinate system

$A_1^0$ Body coordinate system relative to the base coordinate system

$A_2^1$ Souder coordinate system relative to the trunk coordinate system

$A_3^1$ Arm coordinate system relative to the shouder system



Frame of reference (参考系)

Kinematic chain (运动链)， is an assembly of rigid bodies connect by joints to provide constrains motion. 是构件之间连接（运动副）而构成的相对运动的系统

- 闭式运动链（闭链）
- 开链 ，多用在🦾

Kinematic pairs model the hinged and sliding joints fundamental to robotics

Cams and gearing, surface contact joints, called higher pairs

DOF(degrees of freedom) of a kinematic chain



![image-20210113142239259](/Users/kainie/Library/Application Support/typora-user-images/image-20210113142239259.png)









![image-20210118092325256](image-20210118092325256.png)



![image-20210118092335410](image-20210118092335410.png)









![image-20210118112421140](image-20210118112421140.png)



<img src="image-20210122112040446.png" alt="image-20210122112040446" style="zoom: 50%;" />



<img src="image-20210122112114461.png" alt="image-20210122112114461" style="zoom:50%;" />



<img src="image-20210122112134309.png" alt="image-20210122112134309" style="zoom:50%;" />

<img src="image-20210122112153492.png" alt="image-20210122112153492" style="zoom:50%;" />



<img src="image-20210122112210641.png" alt="image-20210122112210641" style="zoom:50%;" />



<img src="image-20210122112228234.png" alt="image-20210122112228234" style="zoom:50%;" />

```python
# KUKA KR9 R900 sixx
# DH parameters

s = {alpha0:      0,  a0:       0, d1:   0.400,
     alpha1:   pi/2,  a1:   0.025, d2:      0.,
     alpha2:     0.,  a2:   0.455, d3:      0.,
     alpha3:   pi/2,  a3:   0.035, d4:    0.42,
     alpha4:   -pi/2,  a4:      0., d5:      0.,
     alpha5:   pi/2,  a5:      0., d6:     0.08,
     alpha6:      0,  a6:      0., d7:       0.}
```



##### TEST

> KUKA KR210

{"A1":64.18, "A2":-102.88, "A3":120.61, "A4":-21.34, "A5":-39.33, "A6":124.21}


![image-20210124215010023](image-20210124215010023.png)

<img src="image-20210124214929129.png" alt="image-20210124214929129"  />

<img src="image-20210124214955652.png" alt="image-20210124214955652" style="zoom:50%;" />





{"A1":67.73, "A2":-96.16, "A3":112.28, "A4":-15.79, "A5":-39.57, "A6":118.49}

![image-20210124215248607](image-20210124215248607.png)













