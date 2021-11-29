---
layout: post
title:  "Rest API based Remote ID communication module"
date:   2021-11-26 12:26:20 -0500
categories: Project explanation
---

The goal of this article is to provide additional insight into the Remote ID based communication module for autonomous UAS navigation. Please refer to the [**main article**](https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/_posts/2021-11-23-A-Remote-ID-based-autonomous-navigation-framework-for-small-UAS.md) for a big picture explanation of the autonomous navigation framework. As mentioned in the main article, the goal of Remote is to provide identification and location information that can be received by other parties. Hence, this module serves two purposes, one is to broadcast identification and location information to the Remote ID server and the other is to receive relevant information from the Remote ID server. Both of these tasks are carried out using an HTTPS communication framework. The Remote ID server is a web service, which can be interacted with using a **REST based API**. REST based APIs are designed to facilitate client interactions with RESTful web services. As seen in the representation below, the interaction involves a request being sent by the client and receiving a resonse from the web service. Based on the clients need, the request can be of different types: GET, PUT, POST, DELETE, etc.

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/2_drone_test_APF_3D.gif" alt="A client-service interaction using REST API" width="800"/> 
</p> 
<p align = "center">
  <b>A client-service interaction using REST API.</b>
</p>  
