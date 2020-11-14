---
title: "European Rover Challenge"
excerpt: "Robotics competition<br/><img src='/images/marsworks_robot.jpg' width='500' height='300'>"
collection: portfolio
---

I am part of the team at the university competing in the [European Rover Challenge](https://roverchallenge.eu/en/main-page/) (ERC), an international space robotics competition, were teams design
and build rovers to perform tasks analogous to those performed by rovers on the surface of Mars and the Moon.

## Role

I am a Robotics Software Engineer within the software sub-team, my responsible is to design and implement
the autonomous navigation system for the rover. This includes the localization, motion planning and control of the rover in a uneven, sandy, Mars like terrain with small hills and valleys
that also contains boulders.
My task is essentially to get the rover to navigate autonomously to a target location safely, quickly, without using GNSS or having a prior map in an unstructured environment.

### 2020

My approach to solving the navigation challenge was as follows:
* Use an **Intel RealSense D435i** depth camera to create a map that should be built as the robot moves towards the target waypoint. [octomap_server](http://wiki.ros.org/octomap_server) 
was used to create the map.
* The octomap was then converted into a [grid_map](https://github.com/ANYbotics/grid_map) to allow for an easy implementation of a path planner.
* An A* search algorithm was implemented to find a path to the goal, only the explored parts of the terrain were part of the map, unknown terrain was assumed to be empty 
until mapped and the correct height information was recorded in the map. The A* heuristic had an extra term to take into account the slope when finding a path.
* The output of the planner was feed into [base_local_planner](http://wiki.ros.org/base_local_planner) to generate a trajectory for the robot to follow, it relayed on a projected 2D map generated from the grid_map.
* localization relied on visual odometry from an **Intel RealSense T256** and completely ignore the wheel odometry due to *assumed* high slippage that will render the data useless.

<div style="text-align:center">
    <img src="/images/marsworks_2020_flowchart.svg" width='400' />
    <figcaption>System diagram.</figcaption>
</div>

<iframe src="https://www.youtube.com/embed/jNA-4pEMKtk"></iframe>

Unfortunately due the pandemic no testing was done on hardware and all the testing was done in simulation on Gazebo as shown in the video above,
the [Canadian Planetary Emulation Terrain 3D Mapping Dataset](http://asrl.utias.utoronto.ca/datasets/3dmap/) was used in the simulated testing, eventually the competition got cancelled as well.

In hindsight I think that there are a couple of problems with the system proposed above:
* Planning with the assumption that the world is empty until visited is not a very good assumption, especially that we are relaying on cameras with 
a small field of view for mapping. This might lead to the robot to not taking the shortest/safest route to the goal.
* Relaying on a visual odometry from a camera with a small field of view (relative to lidar), might cause a lot of drift also the performance of the camera in outdoor
unstructured environments might be poor. Therefore, a better solution is need.

Code can be found [here](https://github.com/Marsworks/rover_nav) on Github. 


### 2021

For this year I am proposing the following system:
* Initially autonomously explore the environment to build a map of the environment using a lidar.
    * SLAM will be performed using [LIO-SAM](https://github.com/TixiaoShan/LIO-SAM).
    * Use a simple heuristic to navigate to maximize the map coverage of the environment. 
* Use as similar approach to the old one of converting the generated map (pointcloud in this case) into a [grid_map](https://github.com/ANYbotics/grid_map) to plan the path.
* Relay on lidar odometry for localization.

Updates will be posted here about the system progress along with any changes in the system architecture (I am sure it will be very different by the competition time).
