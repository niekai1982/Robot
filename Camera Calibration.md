



### Camera Calibration

---

#### Purpose of calibration

1. Validate the accuracy of camera in work distance of 3~4m
2. Get the direction vector of motion of vehicle
3. Get the transformation matrix from camera coordinate to world coordinate

----

#### Parameters of depth camera

> **Device 0: 003008302912**

resolution width: 640
resolution height: 576
principal point x(**ppx**): 315.598328 
principal point y(**ppy**): 331.969116
focal length x(**f_x**): 503.416229
focal length y(**f_y**): 503.437622
radial distortion coefficients:
k1: 3.647457
k2: 2.352810
k3: 0.120397
k4: 3.977356
k5: 3.541886
k6: 0.638353
center of distortion in Z=1 plane(**cod_x**), x: 0.000000
center of distortion in Z=1 plane(**cod_y**), y: 0.000000
tangential distortion coefficient x(**p1**): -0.000066
tangential distortion coefficient y(**p2**): 0.000057
metric radius: 0.000000



> **Device 0: 000204103712**

resolution width: 640
resolution height: 576
principal point x: 326.133362
principal point y: 328.915558
focal length x: 503.709351
focal length y: 503.845337
radial distortion coefficients:
k1: 0.267702
k2: -0.077208
k3: -0.002675
k4: 0.607297
k5: -0.059075
k6: -0.019290
center of distortion in Z=1 plane, x: 0.000000
center of distortion in Z=1 plane, y: 0.000000
tangential distortion coefficient x: 0.000038
tangential distortion coefficient y: -0.000124
metric radius: 0.000000

----

#### Brown-Conrady Calibration Model

- $\text{radial Distortion parameters: }k_1, k_2, k_3 \\ \text{Tangential distortion parameters: }p_1, p_2$

- $X = X_c / Z_c, Y = Y_c / Z_c$
- $r_2 = x^2 + y^2, r_4 = r_2 \times r_2, r_6=r_2 \times r_2 \times r_2 $
- $f = 1 + k_1r_2 + k_2r_4 + k_3r_6$
- $X = X \times f, Y = Y \times f$
- $dx = X + 2p_1XY + p_2(r_2 + 2X^2) \\ dy = Y + 2p_2XY + p_1(r_2 + 2Y^2) \\ X^{'} = dx \\ Y^{'} = dy$
- $u = X^{'}f_x + ppx \\ v = Y^{'}f_y + ppy$

---

#### Pipline of transformation from depth to point cloud

> Azure Kinect SDK, which using Brown Conrady model, and Rational 6KT is deprecated(only supported early internal devices), center of distortion is set to 0 for Brown Conrady model



**path** = ./transformation/main.cpp

**function**: point_cloud_color_to_depth -> k4a_trainformation_depth_image_to_point_cloud()

> Input: transformation_handel, depth_image,calibration_type,point_cloud

**path** = ./src/sdk/k4a.c

**Function**:  k4a_transformation_depth_image_to_point_cloud -> transformation_depth_image_to_point_cloud()

> Input: transformation_handle, depth_image_buffer, depth_image_descriptor, camera(calibration_type), xyz_image_buffer, xyz_image_descriptor)

**path** = ./src/transformation/transformation.c

Function: tranformation_depth_image_to_point_cloud()

Transformation_context = k4a_transformation_t_get_context(transformation_handle)



 -> transformation_depth_image_to_point_cloud_internal(xy_tables, depth_image_data, depth_image_descriptor, xyz_image_data, xyz_image_descriptor)

​	->transformation_depth_to_xyz(xy_tables, depth_image_data, xyz_image_data)

```python
x_table = xy_tables->x_table[i]
z = (int16_t)depth_image_data_uint16[i];
x = (int16_t)(floorf(x_tab * (float)z + 0.5f));
y = (int16_t)(floorf(xy_tables->y_table[i] * (float)z + 0.5f));
```



transformation_create(calibration )

​	-> Transformation_allocate_xy_tables()

 		-> transformation_init_xy_tables(calibration, camera, *buffer, xy_tables_data_size, xy_tables)

​			-> transformation_2d_to_3d(calibration, source_point2d[2], source_depth(1.f), source_camera, target_camera, target_point3d[3], valid)

​				-> transformation_unproject(calibration, point, depth,point3d,valid)

​					->transformation_unproject_internal(calibration,point2d,point3d,valid)



**Depth_xy_tables**

<img src="image-20201230171224580.png" alt="image-20201230171224580"  />

----



Camera Calibration(World Coordinate)

> spacing distance：15 cm

![4](image-20201230170522830.png)



![image-20201230172113954](image-20201230172113954.png)

![image-20201230172231902](image-20201230172231902.png)



![image-20201230172028812](image-20201230172028812.png)

<img src="image-20201231094454934.png" alt="image-20201231094454934" style="zoom:50%;" />

![image-20201231103722881](image-20201231103722881.png)

>  **x,y,z** aix are represent as red, green and blue

Validate Result of Calibration

![image-20201230170836209](image-20201230170836209.png)



Camera Calibration(Motion Vector)

![image-20201230170252198](image-20201230170252198.png)



Plane

```python
Plane(point=Point([ 559.1845914 ,  918.93269202, 3798.01612903]), normal=Vector([-0.00132521,  0.57736837,  0.8164827 ]))
```

Motion Line

```python
Line(point=Point([1473.59050651,  495.05763063, 4099.79166667]), direction=Vector([ 0.00657814, -0.81725962,  0.5762321 ]))
```

$V_z=[-0.00132521, 0.57736837, 0.8164827 ] \\
V_y=[0.00657814, -0.81725962,  0.5762321] \\
V_x=[-0.99997654, -0.00613457,  0.00271497]$



#### Tranformation Matrix R from Camera to World

$R=\begin{bmatrix}V_x\\V_y\\V_z\end{bmatrix}$ T=Plan.Point=$\begin{bmatrix} 559.1845 \\ 918.9326 \\ 3798.0161 \end{bmatrix}$

#### Resolution, Accuracy and Tolerance

$Resolution = \frac{Field\ OF\ View}{Pixel}$

$Accuracy = Resolution \times Effective\ Pixels$



<img src="image-20201231162856458.png" alt="image-20201231162856458"  />



![image-20210329093527009](image-20210329093527009.png)



https://www.keyence.com.cn/ss/products/vision/visionbasics/basic/beginner/

350:500=f:5.2





#### Transformation



##### transformation_3d_to_2d

> input :
>
> - calibrantion
> - Source_point3d[3]
> - Source_camera
> - Target_camera
> - Target_point2d[2]

- Transformation_possible
- Transformation_3d_to_3d
- transformation_project



#### Fill rotation matrix



- rotation = cJSON_GetObjectItem(cJSON *rt, "Rotation")

- translation = cJSON_GetObjectItem(cJSON *rt, "Translation")
- result = fill_array_of_floats(rotation, extrinsic->rotation, )



Calibration_create_fron_raw

> Input:
>
> char *Raw_calibration
>
> 





```cython
static PyMethodDef Pyk4aMethods[] = {
        {"device_open", device_open, METH_VARARGS, "Open an Azure Kinect device"},
        {"device_start_cameras", device_start_cameras, METH_VARARGS, "Starts color and depth camera capture"},
        {"device_stop_cameras", device_stop_cameras, METH_VARARGS, "Stops the color and depth camera capture"},
        {"device_start_imu", device_start_imu, METH_VARARGS, "Starts imu sernsors"},
        {"device_stop_imu", device_stop_imu, METH_VARARGS, "Stops imu sernsors"},
        {"device_get_capture", device_get_capture, METH_VARARGS, "Reads a sensor capture"},
        {"capture_get_color_image", capture_get_color_image, METH_VARARGS, "Get the color image associated with the given capture"},
        {"capture_get_depth_image", capture_get_depth_image, METH_VARARGS, "Set or add a depth image to the associated capture"},
        {"capture_get_ir_image", capture_get_ir_image, METH_VARARGS, "Set or add a IR image to the associated capture"},
        {"device_get_imu_sample", device_get_imu_sample, METH_VARARGS, "Reads an imu sample"},
        {"device_close", device_close, METH_VARARGS, "Close an Azure Kinect device"},
        {"device_get_sync_jack", device_get_sync_jack, METH_VARARGS, "Get the device jack status for the synchronization in and synchronization out connectors."},
        {"device_get_color_control", device_get_color_control, METH_VARARGS, "Get device color control."},
        {"device_set_color_control", device_set_color_control, METH_VARARGS, "Set device color control."},
        {"device_get_color_control_capabilities", device_get_color_control_capabilities, METH_VARARGS, "Get device color control capabilities."},
        {"device_get_calibration", device_get_calibration, METH_VARARGS, "Get device calibration handle."},
        {"device_get_raw_calibration", device_get_raw_calibration, METH_VARARGS, "Get device calibration in text/json format."},
        {"calibration_get_from_raw", calibration_get_from_raw, METH_VARARGS, "Create new calibration handle from raw json."},
        {"transformation_create", transformation_create, METH_VARARGS, "Create transformation handle from calibration"},
        {"transformation_depth_image_to_color_camera", transformation_depth_image_to_color_camera, METH_VARARGS, "Transforms the depth map into the geometry of the color camera."},
        {"transformation_depth_image_to_color_camera_custom", transformation_depth_image_to_color_camera_custom, METH_VARARGS, "Transforms the custom & depth map into the geometry of the color camera."},
        {"transformation_color_image_to_depth_camera", transformation_color_image_to_depth_camera, METH_VARARGS, "Transforms the color image into the geometry of the depth camera."},
        {"transformation_depth_image_to_point_cloud", transformation_depth_image_to_point_cloud, METH_VARARGS, "Transforms the depth map to a point cloud."},
        {"calibration_3d_to_3d", calibration_3d_to_3d, METH_VARARGS, "Transforms the coordinates between 2 3D systems"},
        {"calibration_2d_to_3d", calibration_2d_to_3d, METH_VARARGS, "Transforms the coordinates between a pixel and a 3D system"},
        {"playback_open", playback_open, METH_VARARGS, "Open file for playback"},
        {"playback_close", playback_close, METH_VARARGS, "Close opened playback"},
        {"playback_get_recording_length_usec", playback_get_recording_length_usec, METH_VARARGS, "Return recording length"},
        {"playback_get_calibration", playback_get_calibration, METH_VARARGS, "Extract calibration and create handle from recording"},
        {"playback_get_raw_calibration", playback_get_raw_calibration, METH_VARARGS, "Extract calibration json from recording"},
        {"playback_seek_timestamp", playback_seek_timestamp, METH_VARARGS, "Seek playback file to specified position"},
        {"playback_get_record_configuration", playback_get_record_configuration, METH_VARARGS, "Extract record configuration"},
        {"playback_get_next_capture", playback_get_next_capture, METH_VARARGS, "Get next capture from playback"},
        {"playback_get_previous_capture", playback_get_previous_capture, METH_VARARGS, "Get previous capture from playback"},

        {NULL, NULL, 0, NULL}
    };
```



#### Mode_info

---

> struct
>
> {
>
> unsigned int calibration_image_binned_resolution[2];
>
> int crop_offset[2];
>
> Unsigned int output_image_resolution[2]
>
> } k4a_camera_calibration_mode_info_t

##### Depth

- NFOV_2X2BINNED

{{512, 512}, {96, 90}, {320, 288}}

- NFOV_BINNED

{{1024,1024},{192,180},{640,576}}

- WFOV_2X2BINNED

{{512,512},{0,0},{512,512}}

- WFOV_BINNED

{{1024,1024},{0,0},{1024,1024}}



##### Color

---









