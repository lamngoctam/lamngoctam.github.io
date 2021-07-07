---
title: "Install ROS Melodic on Raspberry Pi4"
date: 2020-05-05
categories:
  - ROS
tags:
  - Pi4
  - ROS
---

### This is tutorial how to install ROS Melodic on Raspberry Pi4B.

## 1.Install Ubuntu 18.04 on Pi4
### 1.1.Official Ubuntu 18.04
1. Download from [ubuntu.com](https://ubuntu.com/download/raspberry-pi)
  - Following their guide but I got the error 
  ```
  [FAILED] Failed to start LOAD Kernel Module
  ```
2. I got the question at [askubuntu.com](https://askubuntu.com/questions/779251/what-to-do-after-failed-to-start-load-kernel-modules) where the author posted the same issue as I have. 
### 1.2.Unofficial Ubuntu 18.04 by James A.Chambers
1. Install Raspbian for Raspberry 4 from [Official Rasperry](https://www.raspberrypi.org/downloads/)
2. We can use a 16GB SD card for updating Firmware for Raspberry 4 using Raspbian!
```
sudo apt-get update && sudo apt-get dist-upgrade -y
sudo rpi-update
```
3. We need to check for bootloader updates. We do this using the new rpi-eeprom utility. The following command will check for updates:
```
sudo rpi-eeprom-update -a
```
4. Download the precompiled image see the releases section located at [Github Unofficial Pi4]https://github.com/TheRemote/Ubuntu-Server-raspi4-unofficial/releases)
4. Using Etcher to burn the image to new SD card (64GB).
5. Insert SD card to Pi4 (connect Keyboard, Mouse, Internet cable and Power)
6. Following commands to install:
```
Username: ubuntu
Password: ubuntu
```
7. Updating the latest kernel/firmware/modules/fixes
```
cd /home 
sudo rm /etc/imgrelease 
sudo ./Updater.sh
```
8. Install Full Ubuntu Desktop Version
```
sudo apt-get update && sudo apt-get dist-upgrade -y && sudo apt-get install ubuntu-desktop -y
```

## 2.Install ROS Melodic on Pi4
### 2.1.Setup ROS Repositories
Link: [wiki.ROS.Raspberry4](http://wiki.ros.org/ROSberryPi/Installing%20ROS%20Melodic%20on%20the%20Raspberry%20Pi)
```
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

### 2.2. make sure your Debian package index is up-to-date:
```
$ sudo apt-get update
$ sudo apt-get upgrade 
```

### 2.3.Install Bootstrap Dependencies
```
$ sudo apt install -y python-rosdep python-rosinstall-generator python-wstool python-rosinstall build-essential cmake
```

### 2.4.Initializing rosdep
```
$ sudo rosdep init
$ rosdep update
```

### 2.5.Installation
Now, we will download and build ROS Melodic.

- Create a catkin Workspace
- In order to build the core packages, you will need a catkin workspace. Create one now:

```
$ mkdir -p ~/ros_catkin_ws
$ cd ~/ros_catkin_ws
```

- Next we will want to fetch the core packages so we can build them. We will use wstool for this. Select the wstool command for the particular variant you want to install:

ROS-Comm: (recommended) ROS package, build, and communication libraries. No GUI tools.
```
$ rosinstall_generator ros_comm --rosdistro melodic --deps --wet-only --tar > melodic-ros_comm-wet.rosinstall
$ wstool init src melodic-ros_comm-wet.rosinstall
```

Desktop: ROS, rqt, rviz, and robot-generic libraries
```
$ rosinstall_generator desktop --rosdistro melodic --deps --wet-only --tar > melodic-desktop-wet.rosinstall
$ wstool init src melodic-desktop-wet.rosinstall
```

- This will add all of the catkin or wet packages in the given variant and then fetch the sources into the ~/ros_catkin_ws/src directory. The command will take a few minutes to download all of the core ROS packages into the src folder. The -j8 option downloads 8 packages in parallel.


- So far, only the ROS-Comm variant has been tested on the Raspberry Pi in Melodic; however, more are defined in REP 131 such as robot, perception, etc. Just change the package path to the one you want, e.g., for robot do:
```
$ rosinstall_generator robot --rosdistro melodic --deps --wet-only --tar > melodic-robot-wet.rosinstall
$ wstool init src melodic-robot-wet.rosinstall
```

Please feel free to update these instructions as you test more variants.

If wstool init fails or is interrupted, you can resume the download by running:
```
wstool update -j4 -t src
```
### 2.6.Resolve Dependencies
Before you can build your catkin workspace, you need to make sure that you have all the required dependencies. We use the rosdep tool for this.

#### 2.6.1.Resolving Dependencies with rosdep
The dependencies should be resolved by running rosdep:
```
$ cd ~/ros_catkin_ws
$ rosdep install -y --from-paths src --ignore-src --rosdistro melodic -r --os=debian:buster
```
This will look at all of the packages in the src directory and find all of the dependencies they have. Then it will recursively install the dependencies.

The --from-paths option indicates we want to install the dependencies for an entire directory of packages, in this case src. The --ignore-src option indicates to rosdep that it shouldn't try to install any ROS packages in the src folder from the package manager, we don't need it to since we are building them ourselves. The --rosdistro option is required because we don't have a ROS environment setup yet, so we have to indicate to rosdep what version of ROS we are building for. Finally, the -y option indicates to rosdep that we don't want to be bothered by too many prompts from the package manager.

After a while rosdep will finish installing system dependencies and you can continue.

### 2.7.Building the catkin Workspace
Once you have completed downloading the packages and have resolved the dependencies, you are ready to build the catkin packages.

Invoke catkin_make_isolated:
```
$ sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic
```
Note: This will install ROS in the equivalent file location to Ubuntu in /opt/ros/melodic however you can modify this as you wish.

With older raspberries it is recommended to increase the add swap space. Also recommended to decrease the compilation thread count with the -j1 or -j2 option instead of the default -j4 option:
```
$ sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic -j2
```
Now ROS should be installed! Remember to source the new installation:
```
$ source /opt/ros/melodic/setup.bash
```
Or optionally source the setup.bash in the ~/.bashrc, so that ROS environment variables are automatically added to your bash session every time a new shell is launched:
```
$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
```
### 2.8.Maintaining a Source Checkout
If we want to keep our source checkout up to date, we will have to periodically update our rosinstall file, download the latest sources, and rebuild our workspace.

#### 2.8.1.Update the workspace
To update your workspace, first move your existing rosinstall file so that it doesn't get overwritten, and generate an updated version. For simplicity, we will cover the *destop-full* variant. For other variants, update the filenames and rosinstall_generator arguments appropriately.

```
$ mv -i melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old
$ rosinstall_generator desktop_full --rosdistro melodic --deps --tar > melodic-desktop-full.rosinstall
```
Then, compare the new rosinstall file to the old version to see which packages will be updated:
```
$ diff -u melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old
```
If you're satisfied with these changes, incorporate the new rosinstall file into the workspace and update your workspace:
```
$ wstool merge -t src melodic-desktop-full.rosinstall
$ wstool update -t src
```
#### 2.8.2.Rebuild your workspace
Now that the workspace is up to date with the latest sources, rebuild it:
```
$ ./src/catkin/bin/catkin_make_isolated --install
```
__If you specified the --install-space option when your workspace initially, you should specify it again when rebuilding your workspace__

Once your workspace has been rebuilt, you should source the setup files again:
```
$ source ~/ros_catkin_ws/install_isolated/setup.bash
```
### References:
1. [Ubuntu18.04 on Pi - Q-engineering](https://qengineering.eu/install-ubuntu-18.04-on-raspberry-pi-4.html)
2. [ROS Melodic on Raspberry 4 - Wiki ROS](http://wiki.ros.org/ROSberryPi/Installing%20ROS%20Melodic%20on%20the%20Raspberry%20Pi)
3. [Starting ROS Melodic on Pi4 - Instructables](https://www.instructables.com/id/Getting-Started-With-ROS-Melodic-on-Raspberry-Pi-4/)
4. [Unofficial Ubuntu 18.04 on Pi4 - Tutorial](https://jamesachambers.com/raspberry-pi-4-ubuntu-server-desktop-18-04-3-image-unofficial/)
5. [Unofficial Ubuntu 18.04 on Pi4 - Github for Image](https://github.com/TheRemote/Ubuntu-Server-raspi4-unofficial/releases)
