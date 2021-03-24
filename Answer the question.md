



\* You are not using the position information gathered with your system for the robot process, e.g. correction of base frames? 

- We use forward transformation to determination robot postion.

\* Humans can’t access the area. Is this correct? Otherwise can you please try to explain what you are using your system for?

- In principle, humans are prohibited from entering the area,.But, in fact,  the area is not completely physically isolated, there has probability of human invasion. 





#### Questions from Mit freundlichen Grüßen:


 \*  Can you please again try to explain the function of your system and the interfaces.



 \*  Can you offer a description of the VW project, such as requested function/intention of the customer, layout with used cameras, camera positions, field of view, process flow





 \*  statement of costs for the necessary parts

- About $10000

 \*  what is needed for commissioning:

- We need arrange a meeting to discuss. 

  \*  how to calibrate

- We use Tasi's hand-calibration to compute the static tranform from a robot's base to the RGBD monitoring system. 



<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210202155100188.png" alt="image-20210202155100188" style="zoom:50%;" />





  \*  how to train parts

- what do you mean by "train parts", which parts?

- If you mean how to train the model, over 500 car images in 8 different color and 3 types were used to train our segmentation models.

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210202160006891.png" alt="image-20210202160006891" style="zoom: 50%;" />

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210202160112203.png" alt="image-20210202160112203" style="zoom: 50%;" />

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210202160141975.png" alt="image-20210202160141975" style="zoom: 50%;" />

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210202160220939.png" alt="image-20210202160220939" style="zoom: 50%;" />

  \*  what can be configured

- Distance threshold of collision detection
- Car segmentation model
- 3D models of tire and car

  \*  interfaces

- Hardware interface: color camera, depth camera, PLC, **Industrial internet**

 \*  Can we use it for other applications, e.g. for tracking (detect position of a car on a conveyor and send the information to a robot controller in real-time?)

- Our car segmentation and location module can be generalized to these scenes.As for the real time, we need to check the hardware configuration(CPU, GPU,...)



#### Questions from Markus:


 \*  Question for future versions, where you want to detect people & include safety features:



  \*  Which safety standards do you plan to comply with? In Germany we often need ISO 10218-2, 15066, 13849 and develop according to IEC 61508

- ISO 13849, ISO 10218-2:2011 and ISO/TS 15066:2016

  \*  You mentioned a reaction time of 300ms – does this include the robot reaction time and stopping motion?

- 300ms  just  including collision detection algorithm, not  the robot reaction time.

  \*  How do you get the safety signals into the robot controller? Do you use a safety BUS? Do you need a PLC?

- We using the Profinet protocol to send safety signal to the robot controller.

  \*  Which is the external certifying body for approval of the safety?

- We install the distance sensor(single-line Lidar ) on the gripper to ensure the safety.

  \*  Which safety functions do you plan on offering? E.g. stop the robot, move away, alert the users, …?

- We offer the following functions, stop the robot, alert user. 

  \*  How do you handle light issues? (e.g. too much or too little light)

- The quality of point cloud mainly depends on the reflectivity of the object.

#### General questions

  \*  What would be an estimated price for a customer?

- ????

  \*  How long do you need for the setup of the system in a new environment? (New place as well as new cars in the scene)

- One month.

  \*  Who would set up the system in the future? Is it designed to be used by the customer? Do you need a system integrator to set it up?

- We need a system integrator to set up the system for the customer.

  \*  What is the measurement principle for the point cloud? Do you use time of flight cameras?

- We use time of flight cameras to obtain 3D data of objects.

  \*  Your system includes a CNN. Do you need to retrain that for new scenarios? How long does that take?

- We only need about 500 samples to retrain our segmentation model.In VW project, it take about  one week time.

