---
title: "ROS2 contributions"
excerpt: "Open source contribution<br/><img src='/images/ros2.jpg' width='500' height='300'>"
collection: portfolio
---

# Overview

Some of the contributions I have to some ROS2 packages, this work could be found on my github.

This work included:
* The typical git workflow of branching, committing, submitting PRs and merging (solving conflicts whenever they occur).
* Code reviews.
* Working with CI. 


# grid_map

[Link](https://github.com/ANYbotics/grid_map) to the repository on Github.

Working on porting grid_map from ROS to ROS2 (see [issue](https://github.com/ANYbotics/grid_map/issues/219)), this is mainly about updating the ROS related APIs, updating CMakeList.txt files as well as doing 
some minor changes along the way. I also set up and maintained the CI through out this piece of work.

All the work completed can be found under the [ros2 branch](https://github.com/ANYbotics/grid_map/tree/ros2), which is
destined to be the main branch one day when ANYbotics decide to make the switch to ROS2.

Huge shout out to [@SteveMacenski](https://github.com/SteveMacenski) and [@maximilianwulf](https://github.com/maximilianwulf) for all the code reviews and
for their guidance through this process from which I have learned a lot.

![grid_map demo](/images/grid_map.gif)
grid_map visualization inside rviz2 in ROS2.


# Navigation2

[Link](https://github.com/ros-planning/navigation2) to navigatoin2 repository on Github.
[Link](https://github.com/ros-planning/navigation.ros.org) to navigation.ros.org repository on Github.

Worked on couple of small PRs fixing bugs and doing small improvements like parameterising all the tf timeouts in the stack. I also worked on documenting all the parameters in the stack,
that included identifying all the parameters in the stack with their default values and namespace then adding them to navigation2 documentation [website](https://navigation.ros.org/).

These were my first open source project contribution, huge thank you to [@SteveMacenski](https://github.com/SteveMacenski) for his support and patience during my first steps in the process.
