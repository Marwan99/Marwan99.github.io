---
title: "Navigation using overhead camera"
excerpt: "University group project<br/><img src='/images/rviz_map.png' width='500' height='300'>"
collection: portfolio
---

## Overview

This is part of university group project focused on Industry 4.0. We were provided with robotic
platforms and robotics arms. Our project was a simulation of a high value low volume factory assemble
process.

## What I worked on

This was my first interaction with ROS. In the ceiling, a webcam was
attached above an arena where the robotic platform was supposed to navigate. I was getting
an mono-colour image from the vision system which I used to create an occupancy grid and
published as the map, the vision system was also supplying me with robot pose which I used
to published as the robot tf and calculate odometry and publish it. I managed to get most of
the things to work in ROS as in the robot was able to plan a trajectory and move to the goal,
however when it got close to the goal the robot started rotating CW and CCW continuously
and I was not able to resolve this problem. I later learned that there is a parameter that could
be set for oscillation control and possible relaxing the goal tolerance a bit could have been a
temporary fix.

## Links

Projects [github](https://github.com/ASC330-Group3/platform_nav) repository