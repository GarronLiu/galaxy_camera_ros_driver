# 描述

- 在大恒水星二代USB3.0相机301-125U3C上通过测试，现可在.launch文件中修改相机分辨率、自动增益、帧率、白平衡、曝光时间以及BINNING模式等参数.
- 欲添加其余参数，可以参考galaxy_camera.cpp中void GalaxyCamera::writeConfig()进行修改，同时可参考GxIAPI.h，因为所有接口已在头文件内定义。

# 调试日志
 
 - 添加了binning模式，在降低相机分辨率的同时保持图像范围不变，减小vinmonos图像处理压力以提高实时性。

# galaxy_camera
ROS wrapper for the galaxy camera made by Daheng Imaging.

Forked from QiayuanLiao/git@github.com:QiayuanLiao/galaxy_camera.git

Dependencies:
- ROS Melodic
- gxiapi

ONLY TESTED ON MER2-302!!!
Updated on 2022.04.10: Already Tested on MER2-301. 

# Getting started 
## Install dependencies
- ROS - http://wiki.ros.org/ROS
- gxiapi: - download `Galaxy_Linux-x86_Gige-U3_32bits-64bits_1.2.1911.9122` from 
http://gb.daheng-imaging.com/CN/Software and install

## Download and build code
This is a ros_packages,you should put it in your ROS workspace.
1. Get the source:
```
git clone git@github.com:QiayuanLiao/git@github.com:QiayuanLiao/galaxy_camera.git
```
2. Make in your workspace
```
catkin_make
source devel/setup.bash
```
## Test
1. Connect the camera by USB, run:
```
roslaunch galaxy_camera MER-139.launch
```
check the image on rqt_image_view.

2. Adjust the params in launch file.


3. Calibrate:
```
rosrun camera_calibration cameracalibrator.py --size 7x5 --square 0.030 image:=/galaxy_camera/image_raw camera:=/galaxy_camera
```

4. More information:
http://wiki.ros.org/image_pipeline

# TODO
- Multi-camera support
- nodelet support
- test on other device
