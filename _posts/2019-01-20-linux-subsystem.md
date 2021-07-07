---
layout: post
title: "How to setup Linux subsystem in Window 10"
tags: [software, linux]
excerpt_separator: <!--more-->
---

---
The blog shows the guide to setup Linux subsystem in Window 10.
<!--more-->

## There are some steps which can help you working on Linux system
- Changing some features in Window as the below images
![image](/assets/linux/LinuxSubsystem2.png)
-
![image](/assets/linux/LinuxSubsystem3.png)
- 
![image](/assets/linux/LinuxSubsystem4.png)
- Next step is downloading the Ubuntu app from Microsoft Store in Window. 

![image](/assets/linux/LinuxSubsystem5.png)

## Working on Ubuntu bash
- If we do `$ ls` command, there is nothing here.
- `$ cd /` then `$ ls` we can see the root of subsystem. __mnt__ is the C folder of Window
- `cd mnt` - `$ ls` - `$ cd C` now we are working on C folder of window
- From `/mnt/c/users/ngoct/Projects` we do `$ sudo apt update` to avoid data corruption if we work on the folder in linux subsystem inside window folder.
- Next is to upgrade `$ sudo apt upgrade`.

## Working on Visual Studio Code on WSL:Ubuntu
- **Install**

  - `tamlam@DESKTOP:/mnt/c/Users/ngoct/Projects/coder$ code.`
  - Create a new file: `$ touch main.cpp`

- **Setting**
  - Fix error:
  ![image](/assets/linux/vs_error1.png)
  ![image](/assets/linux/vs_error2.png)
__Ctrl + Shift + P__ in the tab of __c_cpp_properties.json__, change the default setting to __"compilerPath": "/usr/bin/g++"__

![image](/assets/linux/vscode4.png)

- **Run the code** 

`$ gcc main.cpp -lstdc++ -o main.o` then 
`$ ./main.o` in the Terminal on VSCode
  
![image](/assets/linux/vscode5.png)

## Reference:
- [T.Raj - VSCode on WSL:Ubuntu](https://www.youtube.com/watch?v=TC10i_U4qCo&feature=youtu.be) on Youtube - CppCon channel - 25/6/2019
- [T.Raj - News on VSCode](https://www.youtube.com/watch?v=TC10i_U4qCo&feature=youtu.be) on Youtube - CppCon channel - 18/10/2019
- [Windows 10 Bash & Linux Subsystem Setup](https://www.youtube.com/watch?v=Cvrqmq9A3tA)
