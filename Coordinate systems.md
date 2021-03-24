#### Helios 



![image-20210222171118706](/Users/kainie/Library/Application Support/typora-user-images/image-20210222171118706.png)



#### Azure Kinect



##### Depth Camera



Azure Kinect DK depth camera implements the Amplitude Modulated Continous Wave(AMCW) Time-of-Flight(TOF) principle.



The camera casts modulated illumination in the near-IR(NIR) spectrum onto the scene. 

- Two NIR Laser diodes enabling near and wide field-of-view(FoV) depth modes.

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210222093940830.png" alt="image-20210222093940830" style="zoom:50%;" />

- Global shutter that allows for improved performance in sunlight



The depth camera transmits raw modulated IR images to the host PC. On the PC, the GPU accelerated depth engine software converts the raw signal into depth maps.

- NFoV
- WFoV

- 2x2 binning modes

- unbinned modes



#### Camera Performance

---

- Systematic Error

$E_{systematic}= {}$

- Random Error

##### Invalidation

- Outside of active IR **illumination mask**
- **Saturated** IR signal
- Low IR signal
- Filter outlier
- **Multi-path interference**

##### Illumination Mask

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210222094614680.png" alt="image-20210222094614680" style="zoom:50%;" />



##### Signal Strength

##### Ambiguous depth

Another common case of multipath is pixels that contain the mixed signal from foregroud and background(such as aroud object edges)

<img src="/Users/kainie/Library/Application Support/typora-user-images/image-20210222095822422.png" alt="image-20210222095822422" style="zoom:50%;" />

### Coordinate systems



