---
title: "European Rover Challenge"
excerpt: "Robotics competition<br/><img src='/images/marsworks_robot.jpg' width='500' height='300'>"
collection: portfolio
---

The European Rover Challenge (ERC) is an international space robotics competition, were teams design
and build rovers to perform tasks analogous to those performed by rovers on the surface of Mars and
the Moon. I am part of the team at the university called MarsWorks.


## Task

I am part of the software subteam working as a Robotics Software Engineer. I am responsible for the
navigation, localization and motion planning of the rover in a rough, sandy, Mars like terrain with small hills and valleys.
My task is essentially to get the rover to navigate autonomously to a target location safely, efficiently and quickly, without using GNSS or having a prior map.


### 2020

Our approach to solve the navigation challenge was as follows:
* Use an Intel D435i depth camera to create a map that should be built as the robot moves towards the target waypoint. [octomap_server](http://wiki.ros.org/octomap_server) 
was used to create the map.
* The octomap was then converted into a [grid_map](https://github.com/ANYbotics/grid_map) to allow for an easy implementation of a path planner.
* An A* search algorithm was implemented to find a path to the goal, only the explored parts of the terrain were part of the map, unknown terrain was assumed to be empty 
until mapped and the correct height information was recorded in the map. The A* heuristic had an extra term to take into account the slope when finding the path.
* The output of the planner was feed into [base_local_planner](http://wiki.ros.org/base_local_planner) to generate a trajectory for the robot to follow, it realyed on a projected 2D map generated from the grid_map.
* localization relied on visual odometry from an **Intel T256** and completely ignore the wheel odometry due to *assumed* high slippage that will render the data useless.

Unfortunately due the pandemic no testing was done on hardware and all the testing was done in simulation on Gazebo as shown in the video below, eventually the competition got cancelled as well:(.

<iframe src="https://www.youtube.com/embed/jNA-4pEMKtk"></iframe>



In hindsight I think that there are a couple of problems with the system proposed above:
* Planning with the assumption that the world is empty until visited is not a very good assumption, especially that we are relaying on cameras with 
a small field of view for mapping. This might lead to the robot to not taking the shortest/safest route to the goal.
* Relaying on a visual odometry from a camera with a small field of view (relative to lidar), might cause a lot of drift also the performance of the camera in outdoor
unstructured environments might be poor. Therefore, a better solution is need.


### 2021

For this year we are proposing the following system:
* Initially autonomously explore the environment to build a map of the environment using a lidar.
    * SLAM will be performed using [LIO-SAM](https://github.com/TixiaoShan/LIO-SAM).
    * Use a simple heuristic to navigate to maximize the map coverage of the environment. 
* Use as similar approach to the old one of converting the generated map (pointcloud in this case) into a [grid_map](https://github.com/ANYbotics/grid_map) to plan the path.
* Relay on lidar odometry for localization.

Updates will be posted here about the system progress along with any changes in the system architecture (I am sure it will be very different by the competition time).
