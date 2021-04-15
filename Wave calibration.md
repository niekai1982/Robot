#### Wave calibration





##### CONFIGURATION:

- Cfg.MonitoredRoomDims [-3.0, 3.0, 0.2, 5.0, 0.0, 2.0]
- Cfg.Arena(2).xi_res 0.05
- Cfg.Arena(2).yi_res 0.05
- Cfg.Arena(2).zi_res 0.1





<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210323160617123.png" alt="image-20210323160617123" style="zoom: 67%;" />



tranformation matrix 的求解为非线性方程组，需要找相机标定源代码来获得求解方法



$\left[\begin{matrix}- \sin{\left(\alpha \right)} \sin{\left(\gamma \right)} \cos{\left(\beta \right)} + \cos{\left(\alpha \right)} \cos{\left(\gamma \right)} & - \sin{\left(\alpha \right)} \cos{\left(\beta \right)} \cos{\left(\gamma \right)} - \sin{\left(\gamma \right)} \cos{\left(\alpha \right)} & \sin{\left(\alpha \right)} \sin{\left(\beta \right)} & t_{x} \left(- \sin{\left(\alpha \right)} \sin{\left(\gamma \right)} \cos{\left(\beta \right)} + \cos{\left(\alpha \right)} \cos{\left(\gamma \right)}\right) + t_{y} \left(- \sin{\left(\alpha \right)} \cos{\left(\beta \right)} \cos{\left(\gamma \right)} - \sin{\left(\gamma \right)} \cos{\left(\alpha \right)}\right) + t_{z} \sin{\left(\alpha \right)} \sin{\left(\beta \right)}\\\sin{\left(\alpha \right)} \cos{\left(\gamma \right)} + \sin{\left(\gamma \right)} \cos{\left(\alpha \right)} \cos{\left(\beta \right)} & - \sin{\left(\alpha \right)} \sin{\left(\gamma \right)} + \cos{\left(\alpha \right)} \cos{\left(\beta \right)} \cos{\left(\gamma \right)} & - \sin{\left(\beta \right)} \cos{\left(\alpha \right)} & t_{x} \left(\sin{\left(\alpha \right)} \cos{\left(\gamma \right)} + \sin{\left(\gamma \right)} \cos{\left(\alpha \right)} \cos{\left(\beta \right)}\right) + t_{y} \left(- \sin{\left(\alpha \right)} \sin{\left(\gamma \right)} + \cos{\left(\alpha \right)} \cos{\left(\beta \right)} \cos{\left(\gamma \right)}\right) - t_{z} \sin{\left(\beta \right)} \cos{\left(\alpha \right)}\\\sin{\left(\beta \right)} \sin{\left(\gamma \right)} & \sin{\left(\beta \right)} \cos{\left(\gamma \right)} & \cos{\left(\beta \right)} & t_{x} \sin{\left(\beta \right)} \sin{\left(\gamma \right)} + t_{y} \sin{\left(\beta \right)} \cos{\left(\gamma \right)} + t_{z} \cos{\left(\beta \right)}\\0 & 0 & 0 & 1\end{matrix}\right]$



#### scipy

- scipy.optimize.fsolve

- scipy.optimize.root

Sci

#### sympy

- Solve 



- xi_res 0.05m
- yi_res 0.05m
- zi_res 0.1m

- Mod: 7-MTI

![image-20210325202916256](image-20210325202916256.png)





![image-20210325203939117](image-20210325203939117.png)



![image-20210325233031322](image-20210325233031322.png)



![image-20210325233117274](image-20210325233117274.png)