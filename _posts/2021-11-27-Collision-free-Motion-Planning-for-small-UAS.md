---
layout: post
title:  "Collision free Motion Planning for small UAS"
date:   2021-11-27 10:26:20 -0500
categories: Project explanation
---
In this article, I will discuss the motion planner used in my autonomous UAV navigation project. Please refer to the [**main article**](https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/_posts/2021-11-23-A-Remote-ID-based-autonomous-navigation-framework-for-small-UAS.md) for more information regarding the autonomous navigation project. The goal of a path/motion planner is to create a collision free trajectory to navigate, given obstacle information, both static and dynamic. For the dynamic obstacles, the trajectory prediction from the tracking module serves as an input. Two different motion planners were developed for this project. The first was based on the Artificial Potential Field method, while the second was hierarchical planner composed of the A* algorithm and Finite State Machine based behavioral planner. Both of these methods will be discussed in detail.

## Artificial Potential Field

The basic principle behind the approach involves associating  the goal with a global attractive potential and the obstacles with a local, repulsive potential, like shown in the illustration below. By differentiating the resulting potential field, a force field can be obtained, which can then be integrated to generate a collision free trajectory, as shown below.

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/apf_example.jpg" alt="Illustration demonstrating the APF method" width="400"/> 
</p> 
<p align = "center">
  <b>Illustration demonstrating the APF method.</b>
</p> 
