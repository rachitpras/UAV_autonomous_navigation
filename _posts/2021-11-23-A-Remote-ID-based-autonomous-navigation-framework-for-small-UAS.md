---
layout: post
title:  "A Remote ID based autonomous operations framework for small UAS"
date:   2021-11-23 10:26:20 -0500
categories: Project explanation
---

As per Federal Aviation Agency's (FAA) definition, **remote ID is the ability of a drone in flight to provide identification and location information that can be received by other parties**. As per the FAA, remote ID will play an important role in the integration of autonomous Unmanned Aerial Systems (UAS) operations in the National Aerospace System. The final rule on remote ID will require most drones operating in US airspace to have remote ID capability. Remote ID will provide information about drones in flight, such as the identity, location, and altitude of the drone and its control station or take-off location. Authorized individuals from public safety organizations may request identity of the drone's owner from the FAA. More details on this can be found from [FAA's website](https://www.faa.gov/uas/getting_started/remote_id/).

# A collision-free, autonomous navigation framework using remote ID

Large autonomous systems, such as self driving cars, deploy an array of sensors such as camera, LIDAR, RADAR, etc for perception and SLAM. However, for small UAS, these sensors can be bulky and can substantially reduced its weight carrying capacity. Relying on a one or fewer sensors can reduce reliability. For example, relying just on the camera for obstacle prediciton and tracking, in a sparse but highly dynamic environment will be error prone. Keeping this in mind, in our National Science Foundation (NSF) sponsored project, we have developed a collision-free autonomous navigation framework which uses the Remote ID concept to carry out tasks such as environment perception and obstacle tracking. The developed framework can be used as the primary or support stack. A schematic of the framework is given below. 

<img src="/images/framework_schematic.JPG" alt="Schematic for the UAS navigation framework" width="200"/>

# (![Schematic](/images/framework_schematic.JPG)

