# EU Long-term Dataset with Multiple Sensors for Autonomous Driving 

[Zhi Yan](https://yzrobot.github.io/), [Li Sun](https://sites.google.com/site/lisunspersonalsite/), [Tomas Krajnik](http://labe.felk.cvut.cz/~tkrajnik/), and [Yassine Ruichek](https://www.researchgate.net/profile/Yassine_Ruichek)

[![Build Status](https://travis-ci.org/epan-utbm/utbm_robocar_dataset.svg?branch=baselines)](https://travis-ci.org/epan-utbm/utbm_robocar_dataset)
[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

## Issues

* Radar data: [13](https://github.com/epan-utbm/utbm_robocar_dataset/issues/13)
* Vehicle position ground-truth provided by GPS-RTK: [1](https://github.com/epan-utbm/utbm_robocar_dataset/issues/1), [7](https://github.com/epan-utbm/utbm_robocar_dataset/issues/7)

## Dataset

[https://epan-utbm.github.io/utbm_robocar_dataset/](https://epan-utbm.github.io/utbm_robocar_dataset/)

## Baselines

We forked the implementation of the following state-of-the-art methods and experimented (with minor changes) with our dataset:

* Pose Estimation: https://github.com/tu-darmstadt-ros-pkg/hector_localization
* Lidar odometry: https://github.com/laboshinl/loam_velodyne
* Lidar odometry: https://github.com/RobustFieldAutonomyLab/LeGO-LOAM
* To be continued ...

All users are more than welcome to commit their results.

*Ground-truth trajectories recorded by GPS/RTK*

## hector_pose_estimation (pose estimation)

![hector_pose.png](images/hector_pose.png)

### How to play

```shell
roslaunch utbm_pose_estimation.launch bag:=path_to_your_rosbag
```

```utbm_pose_estimation.launch``` is [here](baselines/utbm_pose_estimation/launch/utbm_pose_estimation.launch).

### Evaluation

First of all, you should have something like this:https://yzrobot.github.io/

![hector_rosgraph.png](images/hector_rosgraph.png)


Then, ```/fix/pose```([geometry_msgs/PoseStamped](http://docs.ros.org/api/geometry_msgs/html/msg/PoseStamped.html)) ihttps://yzrobot.github.io/s the estimated robot pose (6DOF) based on the GPS data.

## loam_velodyne (lidar odometry)

![loam_map.png](images/loam_map.png)

### How to play

```shell
roslaunch loam_velodyne loam_velodyne_utbm.launch bag:=path_to_your_rosbag
```

```loam_velodyne_utbm.launch``` is [here](baselines/loam_velodyne/launch/loam_velodyne_utbm.launch).

### Evaluation

First of all, you should have something like this:

![loam_rosgraph.png](images/loam_rosgraph.png)

Then, ```/aft_mapped_to_init```([nav_msgs/Odometry](http://docs.ros.org/melodic/api/nav_msgs/html/msg/Odometry.html)) is the output lidar odometry that needs to be evaluated.

Single Velodyne HDL-32E (left)

![loam_velodyne_20180719.png](baselines/results/loam_velodyne/loam_velodyne_20180719.png)

## LeGO-LOAM (lidar odometry)

1. Minor changes w.r.t. LeGO-LOAM ([Issue #9](https://github.com/epan-utbm/utbm_robocar_dataset/issues/9), thanks to robot54)

![lego_map.png](images/lego_map.png)

### How to play

```shell
roslaunch lego_loam lego_loam_utbm.launch bag:=path_to_your_rosbag
```

```lego_loam_utbm.launch``` is [here](baselines/LeGO-LOAM/LeGO-LOAM/launch/lego_loam_utbm.launch).

### Evaluation

First of all, you should have something like this:

![lego_rosgraph.png](images/lego_rosgraph.png)

Then, ```/aft_mapped_to_init```([nav_msgs/Odometry](http://docs.ros.org/melodic/api/nav_msgs/html/msg/Odometry.html)) is the output lidar odometry that needs to be evaluated.

Single Velodyne HDL-32E (left)

![lego_loam_20180719.png](baselines/results/lego_loam/lego_loam_20180719.png)
![lego_loam_loop_closure_20180719.png](baselines/results/lego_loam/lego_loam_loop_closure_20180719.png)


