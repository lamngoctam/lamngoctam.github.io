---
title: "Using Kinect XBOX 1473 with ROS"
date: 2020-10-10
categories:
  - ROS
tags:
  - KinectXBOX
---

### What is the Kinect XBOX 1473 sensor

### Install Kinect in ROS
We should install library and packages with openni
```
$ sudo apt-get install ros-melodic-openni-camera ros-melodic-openni-launch
$ rosstack profile && rospack profile
```

You can see the list of directories
``` 
0.083792   /opt/ros/melodic/share
0.009981   /home/tamlam/catkin_ws/src
0.007983   /home/tamlam/mybot_ws/src
0.006549   /home/tamlam/mybot_ws/src/geometry2
0.006091   /home/tamlam/catkin_ws/src/hector_slam
0.001408   /home/tamlam/rgbdslam_catkin_ws/src
0.000619   /home/tamlam/catkin_ws/src/ros_best_practices
0.000210 * /opt/ros/melodic/share/doc
0.000011 * /opt/ros/melodic/share/doc/liborocos-kdl
```
Then run the below commands to launch the library
```
$ rosrun openni_camera openni_node
$ roslaunch openni_launch openni.launch
```
We can check the topics by 
```
$ rostopic list
/camera/depth/image
/camera/rgb/image_color
...
```
To display depth/color image
```
$ rosrun image_view image_view image:=/camera/depth/image
$ rosrun image_view image_view image:=/camera/rgb/image_color
```



### References:
1. [OpenNI](https://github.com/OpenNI/OpenNI)

