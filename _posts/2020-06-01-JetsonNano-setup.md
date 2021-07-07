---
layout: post
title: "Jetson Nano Setup"
tags: [Jetson Nano, Linux]
excerpt_separator: <!--more-->
---

---
The blog shows the very first steps for setting up the Jetson Nano.
<!--more-->

### Swaping memory

- Check System Monitor: see the Memory (with 3.9GB) and Swap (normally with 2GB)
- Check the link to see how is the maximum memory can swap: https://help.ubuntu.com/community/SwapFaq
- Can swap maximum 8GB

- Create the Swap File:
We will create a 8GB file (/mnt/8GiB.swap) to use as swap:
```
sudo fallocate -l 8g /mnt/8GB.swap
```
fallocate size suffixes: g = Giga, m = Mega, etc. (See man fallocate).

We need to set the swap file permissions to 600 to prevent other users from being able to read potentially sensitive information from the swap file.

sudo chmod 600 /mnt/8GB.swap
Format the file as swap:
```
sudo mkswap /mnt/8GB.swap
```
Enable use of Swap File
```
sudo swapon /mnt/8GB.swap
```
Enable Swap File at Bootup
Add the swap file details to /etc/fstab so it will be available at bootup:
```
echo '/mnt/1GiB.swap swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

- You can use the following website to get the swap manually back into RAM: https://help.ubuntu.com/community/SwapFaq

### Install TensorFlow
- https://www.pyimagesearch.com/2019/05/06/getting-started-with-the-nvidia-jetson-nano/
 
His guide is to install **tensorflow-gpu==1.13.1+nv19.3** (40 mins)
```
$ pip install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu==1.13.1+nv19.3
```
then (35 mins)
```
$ pip install scipy
$ pip install keras
```
- From JK Jung Blog: https://jkjung-avt.github.io/jetpack-4.4/

  - Installing tensorflow-1.15.2
  - Reference (official documentation from NVIDIA): Installing TensorFlow For Jetson Platform 
  (https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html)

  - At the time of this writing, NVIDIA has provided pip wheel files for both **tensorflow-1.15.2 and tensorflow-2.1.0 (https://developer.download.nvidia.com/compute/redist/jp/v44/tensorflow/)**. 
  I used 1.15.2 since my **TensorRT Demo #3: SSD** only works for **tensorflow-1.x**.
  - just followed instructions on the official documentation, but skipped installation of “protobuf”. 
  (I already built and installed “protobuf-3.8.0” in the opencv section.)
  ```
    $ sudo apt-get install -y libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev liblapack-dev libblas-dev gfortran
    $ sudo pip3 install -U pip testresources setuptools
    $ sudo pip3 install -U numpy==1.16.1 future mock h5py keras_preprocessing keras_applications gast futures pybind11
    $ sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v44 tensorflow==1.15.2
  ```
  - At this point, I tested and made sure “import tensorflow as tf” worked OK in python3.
