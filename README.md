# ALPHA BOT PROJECT
![Robot_image](https://github.com/arubedaq/HomeCollectionRobot/blob/main/images/PlanteamientoGeneral.png)

## Project description
This project is based on the existing repository: https://github.com/ros-mobile-robots/diffbot. All the documentation and results of the project are available in "AlphaBotPlanner_Memoria.pdf".

This project implements the entire navigation stack for an autonomous ground mobile robot:

- Localization: We present some localization methods:
    - Localization based on the "robot_localization" package (https://docs.ros.org/en/melodic/api/robot_localization/html/index.html), which fuses information from the following sensors:
        - Model-based odometry
        - LiDAR odometry, using the ROS package "scan_tools" (https://wiki.ros.org/scan_tools).
        - IMU
        - AMCL (Adaptive Monte Carlo Localization, http://wiki.ros.org/amcl) using LiDAR readings and the map    
    Three versions are available, following the ROS REP105 standard (https://www.ros.org/reps/rep-0105.html).

Ground Truth-based Localization: We use the actual robot position for debugging and some experiments.

![EKF_image](https://github.com/arubedaq/HomeCollectionRobot/blob/main/images/EKF.png)

- Path Planning: We have developed a path planning algorithm based on Dijkstra. This algorithm relies on information from a global cost map, so it will not take into account any possible map modifications during runtime; it will be treated as static. The planner has been programmed by ourselves, but to achieve this, we need to use a cost map based on a previously created global map using the ROS package "gmapping" (http://wiki.ros.org/gmapping).

![Planner_image](https://github.com/arubedaq/HomeCollectionRobot/blob/main/images/Planner.png)

- High-Level Control (Path Following): The developed high-level control algorithm is a path following algorithm based on Pure Pursuit. From it, we have made a series of specific adaptations for our configuration and have proposed some simplifications for its implementation.

![PurePursuit_image](https://github.com/arubedaq/HomeCollectionRobot/blob/main/images/PurePursuit.png)

Next, we present a series of graphs from a representative experiment:

![Experiment_image](https://github.com/arubedaq/HomeCollectionRobot/blob/main/images/ExperimentoRepresentativo.png)


## Tested Platforms
This ROS package has been tested in the following environments:
- Native Ubuntu 18 - ROS 1 Melodic
- VirtualBox and VMware virtual machines 
- WSL2

## Installation
### From Ubuntu
This installation method will also work for WSL2 and virtual machines.

- Prerequisites: Ubuntu 18 - ROS Melodic
- If selected: WSL2 or virtual machine installed and running Ubuntu 18 - ROS Melodic

```
cd ~ # IT IS IMPORTANT TO CLONE REPO IN 
git clone https://github.com/arubedaq/alpha-bot.git
cd alpha-bot
rosdep install --from-paths src --ignore-src -r -y
catkin_make
source devel/setup.sh
roslaunch alpha_bot_simulation sim.launch
```

## Development
This is intended as a deliverable for a university course. Therefore, probably will not receive any updated from now on. However, feel free to fork it and expand its functionalities ;)

## Authors
Isaac Rodríguez García

Álvaro García Lora

Sergio León Doncel

Arturo Renato Úbeda Quilón



