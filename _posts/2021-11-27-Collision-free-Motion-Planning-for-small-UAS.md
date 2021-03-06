---
layout: post
title:  "Collision free Motion Planning for small UAS"
date:   2021-11-27 10:26:20 -0500
categories: Project explanation
---
In this article, I will discuss the motion planner used in my autonomous UAV navigation project. Please refer to the [**main article**](https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/_posts/2021-11-23-A-Remote-ID-based-autonomous-navigation-framework-for-small-UAS.md) for more information regarding the autonomous navigation project. The goal of a path planner is to create a collision free trajectory to navigate, given mission information such as origin and goal location, and obstacle information, both static and dynamic. For the dynamic obstacles, the trajectory prediction from the tracking module serves as an input. Two different motion planners were developed for this project. The first was based on the Artificial Potential Field (APF) method, while the second was hierarchical planner composed of the A* algorithm and Behavior Tree based behavioral planner. Both of these approaches will be discussed in detail.

## Artificial Potential Field method

The basic principle behind the approach involves associating  the goal with a global attractive potential and the obstacles with a local, repulsive potential, like shown in the illustration below. By differentiating the resulting potential field, a force field can be obtained, which can then be numerically integrated to generate a collision free trajectory, as shown below.

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/apf_example.jpg" alt="Illustration demonstrating the APF method" width="400"/> 
</p> 
<p align = "center">
  <b>Illustration demonstrating the APF method.</b>
</p> 

Compared to other graph based and sampling based methods such as A* and RRT, the APF method is computationally far more efficient, as it doesn't apply any expensive search mechanism. On the other hand, the method provides no guarantee in successfully generating a trajectory even if one exists. For example, if there is a local minima in the potential field, the generated trajectory gets trappend at that minima and fails to successfully generate a trajectory to the goal. Moreover, there is no guarantee that the generated trajectory is optimal in terms of length and can result in longer trajectories even if shorter ones are present. On the other hand, A* and RRT are much more robust and are known to produce more optimal trajectories.

## Hierarchical Planner (A* + Behavior Tree)

As discussed in the previous section, while the A* algorithm has superior performance compared to the APF method, it is computationally expensive. When path planning needs to be done considering dynamic obstacles, it needs to be done repeatedly keeping the updated information of the dynamic obstacles in mind. Hence, for real time implementation, A* proves to be expensive. However, we overcome this issue by using the A* algorithm just once in the beginnning to generate a feasible trajectory. Only the static obstacles' locations are considered by A*. Following this generated trajectory ensures that the drone doesn't collide with any static obstacles. In order to deal with dynamic obstacles, a behavior tree based task switching mechanism. A behavior tree is a structure that enables switching between tasks in a modular and hierarchical manner. In our project, behavior tree shown in the figure below has been used. The idea behind the behavior tree is to first check whether a collision is possible with other dynamic obstacles over the next planning loop, if the drone continues to follow the waypoints generated by the A* algorithm. If a possibility of collision is detected, then the behavior tree decides whether a collision would occur if the drone decides to hover. If a possibility of collision due to hover is detected, then the drone will go for a collision avoidance maneuver, else it will hover. If no collision is detected under any circumstances, then the drone would simply continue to track the waypoints generated by A*. In interest of keeping the details to a minimum, I haven't discussed the details of the collision detection funciton and and the collision avoidance mechanism. Interested reader can contact me via email for additional info. More info shall be put up at a later stage. 

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/behavior_tree.JPG" alt="Behavior Tree based hierarchical planner" width="400"/> 
</p> 
<p align = "center">
  <b>Behavior Tree based hierarchical planner.</b>
</p> 

Both the planners can be seen in action below, where animations of a simulated scenario are presented. From the animations it can be seen that the trajectory generated by APF method is sub-optimal when compared to the hierarchical planner. More scenarios and results will be put up soon.

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/2_drone_test_APF_3D.gif" alt="Autonomous UAV navigation using the APF planner" width="800"/> 
</p> 
<p align = "center">
  <b>Autonomous UAS navigation using the APF planner.</b>
</p>  


<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/2_drone_test_BP_3D.gif" alt="Autonomous UAV navigation using the hierarchical planner" width="800"/> 
</p> 
<p align = "center">
  <b>Autonomous UAV navigation using the hierarchical planner.</b>
</p>  
