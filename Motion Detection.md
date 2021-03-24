



### Motion Detection

---





#### Method Proposed

---

![image-20210222132316148](image-20210222132316148.png)

- Picture 1 is frame to background subtractor
- Picture 2 is frame of motion object
- Picture 3 is motion object segmentation



![image-20210202004240996](image-20210202004240996.png)

![image-20210202004121291](image-20210202004121291.png)

![image-20210202004043481](image-20210202004043481.png)

#### MOG2 background subtractor

---

> 20 frames

Why there has noise points? Gaussian noise?

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210201104759173.png" alt="image-20210201104759173" style="zoom:67%;" />

![image-20210201133531074](/Users/kainie/Library/Application Support/typora-user-images/image-20210201133531074.png)



<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210201104837035.png" alt="image-20210201104837035" style="zoom:67%;" />

#### Camera coordinate & World geometry

---

![image-20210204232424392](image-20210204232424392.png)





#### Tracking (DeepSort)

---

<img src="image-20210201153152170.png" alt="image-20210201153152170" style="zoom: 67%;" />

<img src="image-20210201153159788.png" alt="image-20210201153159788" style="zoom:67%;" />

<img src="image-20210201153210751.png" alt="image-20210201153210751" style="zoom:67%;" />

<img src="image-20210201153221132.png" alt="image-20210201153221132" style="zoom:67%;" />

<img src="image-20210201153131990.png" alt="image-20210201153131990" style="zoom:67%;" />







![image-20210204232441366](image-20210204232441366.png)





#### RESULT & Problem

---

> Ver2.0



- IDX=70, Motion Area Threshold = 1000

<img src="image-20210205102238903.png" alt="image-20210205102238903" style="zoom:50%;" />

- IDX=80, Motion Area Threshold = 1000

<img src="image-20210205102021601.png" alt="image-20210205102021601" style="zoom:50%;" />

- IDX=90, Motion Area Threshold = 1000

<img src="image-20210205101837038.png" alt="image-20210205101837038" style="zoom:50%;" />

- IDX=100, Motion Area Threshold = 1000

<img src="image-20210205101201657.png" alt="image-20210205101201657" style="zoom: 33%;" />

- IDX=110, Motion Area Threshold = 1000

<img src="image-20210205100710012.png" alt="image-20210205100710012" style="zoom:50%;" />

- DX=120, Motion Area Threshold = 1000

<img src="image-20210205100856713.png" alt="image-20210205100856713" style="zoom: 33%;" />



- DX=130, Motion Area Threshold = 1000

<img src="image-20210205101025042.png" alt="image-20210205101025042" style="zoom:50%;" />



- IDX=140, Motion Area Threshold = 1000

<img src="image-20210205104239124.png" alt="image-20210205104239124" style="zoom: 33%;" />

- IDX=150, Motion Area Threshold = 1000

<img src="image-20210205104453538.png" alt="image-20210205104453538" style="zoom: 33%;" />

- IDX=160, Motion Area Threshold = 1000

<img src="image-20210205104607542.png" alt="image-20210205104607542" style="zoom: 50%;" />

- IDX=190, Motion Area Threshold = 1000

<img src="image-20210205104853594.png" alt="image-20210205104853594" style="zoom:50%;" />

- IDX=190, Motion Area Threshold = 1000

<img src="image-20210205105018650.png" alt="image-20210205105018650" style="zoom:50%;" />

<img src="image-20210205105201727.png" alt="image-20210205105201727" style="zoom: 33%;" />

- IDX=250, Motion Area Threshold = 1000

<img src="image-20210205105827580.png" alt="image-20210205105827580" style="zoom:50%;" />

<img src="image-20210205105903461.png" alt="image-20210205105903461" style="zoom:50%;" />

- IDX=270, Motion Area Threshold = 1000

<img src="image-20210205110021599.png" alt="image-20210205110021599" style="zoom:50%;" />

<img src="image-20210205110111055.png" alt="image-20210205110111055" style="zoom:50%;" />

<img src="image-20210205110134707.png" alt="image-20210205110134707" style="zoom:50%;" />

<img src="image-20210205110220277.png" alt="image-20210205110220277" style="zoom:50%;" />

#### Next

- 毫米波雷达和图像融合

![image-20210206154626131](image-20210206154626131.png)



<img src="image-20210222132958813.png" alt="image-20210222132958813" style="zoom:50%;" />



- 3D point unproject to RGB & tracking target initialization

​	

<img src="image-20210222134345183.png" alt="image-20210222134345183"  />

![image-20210222133925575](image-20210222133925575.png)

![image-20210222134147580](image-20210222134147580.png)

![image-20210222134642880](image-20210222134642880.png)



- 机器人、Camer、毫米波雷达信号的同步

机器人





![image-20210222144712096](image-20210222144712096.png)





![image-20210301210548450](image-20210301210548450.png)