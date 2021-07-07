---
title: "Path planning"
date: 2019-03-01
categories:
  - courses
  - papers
tags:
  - robotics
  - PathPlanning
---

## Course 6: Path Planning from Udacity

Path planning routes a vehicle from one point to another, and it handles how to react when emergencies
arise. The Mercedes-Benz Vehicle Intelligence team will take you through the three stages of path
planning. First, you’ll apply model-driven and data-driven approaches to predict how other vehicles on the
road will behave. Then you’ll construct a finite state machine to decide which of several maneuvers your
own vehicle should undertake. Finally, you’ll generate a safe and comfortable trajectory to execute that
maneuver.

Lesson | Title | Description
--- | --- | ---
1 | Search | In this lesson you will learn about discrete path planning and algorithms for solving the path planning problem.
2 | Prediction | In this lesson you'll learn how to use data from sensor fusion to generate predictions about the likely behavior of moving objects.
3 | Behavior Planning | In this lesson you'll learn how to think about high level behavior planning in a self-driving car.
4 | Trajectory Generation | In this lesson, you’ll use C++ and the Eigen linear algebra library to build candidate trajectories for the vehicle to follow.

## Discrete Path Planning
- [Text book by Steven M. LaValle - University of Illinois](http://planning.cs.uiuc.edu/ch2.pdf)

## Object Manipulation
- [ ] Contact Kinematics
- [ ] Kinematic Constraints
  - Reading the Thesis: 2011 PhD Thesis - `Planning and Control Methods for Robotics Manipulation Task with Non-Negligible Dynamics` This thesis used definition from Montana paper.

## Ebooks
`D:\2018 BioRobotics Lab\Academic topics\Topic on ROBOTIC Path Planning`
- [[Nikolaus Correll] Introduction on Autonomous Robotic]()
- [[Roland_Siegwart] Introduction Autonomous Mobile Robots 2nd]()
- [[Giuseppe_Carbone] Motion and Operation Planning of Robotic Systems ]()
- [[Howie_Choset et] Principles of Robot motion - Theory, Algorithms and Implemenation]()

## Paper
- [**Multi-Robot Coordinated Planning in Confined Environments under Kinematic Constraints**](https://www.raas.ece.vt.edu/wordpress/wp-content/papercite-data/pdf/1910.03101.pdf) 
`Runing fast-dRRT in Matlab`
- [**Distributed Attack-Robust Submodular Maximization for Multi-Robot Planning**](https://arxiv.org/pdf/1910.01208.pdf)
` They demonstrate DRM’s performance in both Gazebo and MATLAB simulations, in scenarios of active target tracking with swarms of robots.`
- [**Resilient Active Target Tracking with Multiple Robots**](https://arxiv.org/pdf/1809.04032.pdf)
- **View Planning and Navigation Algorithms for Autonomous Bridge Inspection with UAVs**

`A few of the mentioned works look at **planning paths** for the UAV for infrastructure inspection. Scherer and Yoder [6] plan paths incrementally along arbitrary structures. This however may lead to a non-optimal path of the arbitrary structure. We are able to guarantee an optimal solution for coverage of a 3D surface. Alexis et al. [8] plan by combining Traveling Sales Person (TSP) and Rapidly-exploring Random Tree (RRT*) to obtain a close-to-optimal solution. Our algorithm guarantees optimality as well as conducts path planning for UAVs that are not in contact with the structure of interest. Hollinger et al. [9] implement two planners for non-adaptive and adaptive classification. The authors use object detection to decide on view points that would best help to classify objects or defects on a structure. This planner looks at planning for a singular area to get the best view where as our planner looks at optimal planning for a large 3D structure like a bridge.`

## Software or Library
- [ ] [VisiLibity1 - Planar Visibility Computations](https://karlobermeyer.github.io/VisiLibity1/) 
*VisiLibity1 is a free open source C++ library for 2D floating-point visibility algorithms, path planning, and supporting data types.*

This software was used in the paper [Tree Search Techniques for Minimizing Detectability and Maximizing Visibility](https://www.raas.ece.vt.edu/wordpress/wp-content/papercite-data/pdf/zhang2019tree.pdf)
- [ ] [Fast-dRRT](https://github.com/CMangette/Fast-dRRT) (> Cloned to Labtop)
  
- [ ] [**Gazebo** ]()
  - Papers do experiments in Gazebo: 
  
    [View Point Planning for Inspecting Static and Dynamic Scenes with Multi-Robot Teams](https://vtechworks.lib.vt.edu/bitstream/handle/10919/78807/Budhiraja_AK_T_2017.pdf?sequence=1&isAllowed=y) `The resulting algorithm was also tested in the Gazebo simulation environment (Figure 2.4) using two Pioneer 3DX robots fitted with a limited field-of-view angle camera. The robots emulate an omnidirectional camera by rotating in place whenever they reach a new vertex. Table 2.2 shows the comparison between the lengths of the tours on the input graph and the actual distance traveled by the robots in the Gazebo simulation environment. The actual distances are shorter since the robot is not restricted to move on the input graph in the polygonal environment.`
    [Competitive Algorithms and System for Multi-Robot Exploration of Unknown Environments](https://vtechworks.lib.vt.edu/bitstream/handle/10919/78847/Premkumar_A_T_2017.pdf?sequence=1&isAllowed=y)
    
 ## References
- [6] [Autonomous exploration for infrastructure modeling with a micro aerial vehicle]() 
- [7] [Autonomous navigation and mapping for inspection of penstocks and tunnels with mavs]()
- [8] [Aerial robotic contact-based inspection: planning and control]()
- [9] [Active classification: Theory and application to underwater inspection]()
