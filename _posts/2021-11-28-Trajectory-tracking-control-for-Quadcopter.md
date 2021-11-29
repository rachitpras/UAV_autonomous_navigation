---
layout: post
title:  "Trajectory tracking control for Quadcopters"
date:   2021-11-28 10:26:20 -0500
categories: Project explanation
---
The goal of a trajectory tracking controller is to determine the appropriate control actuation that will enable the ego-vehicle to track the planned trajectory generated by the motion planner. Based on our literature survey, two different control architectures were experimented with. The first was PID based and the second was Model Predictive Control  (MPC) based.  
## PID based trajectory tracking control for Quadcopters