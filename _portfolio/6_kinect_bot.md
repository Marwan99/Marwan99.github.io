---
title: "kinect_bot"
excerpt: "Robotics project<br/><img src='/images/kinect_bot.jpg' width='500' height='300'>"
collection: portfolio
---

## Overview

This is a differential-drive robotic platform trying to mimic the turtlebot for learning about ROS, it is a project I am working on with a friend for us to learn about ROS, specifically navigation.

![kinect_bot](/images/kinect_bot.jpg)

Kinect_bot during construction.

The robot is equipped with kinect sensor, an L298N H-bridge for driving two brushed geared DC motors with encoders for feedback, a raspberry Pi for runROS, an Arduino for low level motor PID control and encoder interface. The motor controller were written from scratch and tuned, the arduino is interfacing with the ROS thrthe raspberry pi via rosserial. The depth image from the kinect is converted into laser scans then used for SLAM.
Currently, using gmapping the robot is able to create mThe plan is to explore packages such as cartographer and RTAB for building maps, adding IMU and using EKF for better localization and of course navigate using these maps while playing with the planner different parameters and explore the effects of changing them. Thian open ongoing project.

## Links

- kinect_bot [Github repository](https://github.com/Marwan99/kinect_bot)
