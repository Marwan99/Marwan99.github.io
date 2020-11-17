---
title: "Long-term Visual Teach-and-Repeat Navigation using a Single Topological Map"
excerpt: "Autonomous Navigation"
collection: publications
---

This is part of research conducted on Teach-and-Repeat Outdoor Autonomous Navigation in the [AdMall project](https://sites.google.com/view/fairsapce-admall/).
The research was investigating day to night Teach-and-Repeat outdoor navigation using monocular vision with a focus using deep-learned descriptors
and fisheye cameras to handle changes in the lighting conditions as well as aggressive manuevers.

<iframe src="https://www.youtube.com/embed/4oTsYiRGueI"></iframe>

## Contributions

- Implemented a PID controller to control the heading of the robot based on the output of the NN.
- Running experiment's on the physical robot in outdoors and performing data collection.
- Post precessing the collected data to obtain the trajectories from the different experiments, that included:
    * Running a SLAM algorithm to get the trajectories to act as ground truth for evaluating the system.
    * The robot start pose was kept constant between the different experiments, however the SLAM system initialized the robot's yaw differently
        for each experiment so there was a rotation between the generated maps and trajectories. Since we needed to compare the trajectories, I wrote 
        tool that used ICP to get the transformation between the pointclouds of the maps generated from SLAM and used it to transform the trajectories 
        to the same frame.
- Setting up the robot hardware:
    * Designing and manufacturing the sensors and laptop mounting hardware.
    * Setting up the motor drivers to run in closed loop.
- Helped with the paper submitted for ICRA 2021 (currently under review).

<div style="text-align:center">
    <img src="/images/jaguar.jpg" width='400' />
    <figcaption>Jaguar and it's sensor suit.</figcaption>
</div>

- Navigation code repository [github](https://github.com/kevinlisun/jaguar_nav)
- ICP aligning tool [github](https://github.com/Marwan99/pointcloud_align)
