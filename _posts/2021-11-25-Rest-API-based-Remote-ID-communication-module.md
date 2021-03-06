---
layout: post
title:  "Rest API based Remote ID communication module"
date:   2021-11-26 12:26:20 -0500
categories: Project explanation
---

The goal of this article is to provide additional insight into the Remote ID based communication module for autonomous UAS navigation. Please refer to the [**main article**](https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/_posts/2021-11-23-A-Remote-ID-based-autonomous-navigation-framework-for-small-UAS.md) for a big picture explanation of the autonomous navigation framework. As mentioned in the main article, the goal of Remote ID is to provide identification and location information that can be received by other parties. Hence, this module serves two purposes, one is to broadcast identification and location information to the Remote ID server and the other is to receive relevant information from the Remote ID server. Both of these tasks are carried out using an HTTPS communication framework. The Remote ID server is a web service, which can be interacted with using a **REST based API**. REST based APIs are designed to facilitate client interactions with RESTful web services. As seen in the representation below, the interaction involves a request being sent by the client and receiving a resonse from the web service. Based on the clients need, the request can be of different types: GET, PUT, POST, DELETE, etc. A GET request involves the client requesting information from the web service. PUT/POST requests involve the client providing information to the web service and so on. 

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/REST_API.JPG" alt="A client-service interaction using REST API" width="300"/> 
</p> 
<p align = "center">
  <b>A client-service interaction using REST API.</b>
</p>  

## REST API based communication
Coming back to the Remote ID communication module, the purpose of broadcasting information to the remote ID server is met using the POST request. The body of the POST request compromises of a JSON message in a format shown below. The purpose of requesting information from the remote ID server is met using the GET request, wherein the message contains the GPS information of the ego-vehicle and the remote ID server returns the trajectory history of other drones in the vicinity and static obstacle information in GeoJSON format. 

<p align = "center">
  <img src="https://github.com/rachitpras/UAV_autonomous_navigation/blob/main/images/Remote_ID_message.JPG" alt="Format of message required to be broadcasted to the Remote ID server (source: FAA)" width="200"/> 
</p> 
<p align = "center">
  <b>A Format of message required to be broadcasted to the Remote ID server (source: FAA).</b>
</p>  

## Implementation
The module was first developed in Python (using the [requests library](https://docs.python-requests.org/en/latest/)) and tested using [Postman](https://www.postman.com/). Postman is a tool which greatly improves the process of API development and testing. Once the framework was tested, the code was converted to C++ for embedded real time implementation. REST API requests in C/C++ are carried out using [cURL](https://curl.se/). However, [C++ requests](https://docs.libcpr.org/) was used for easy implementation. C++ Requests is a simple wrapper around cURL inspired by the Python Requests project, which provides a cleaner and easy to read syntax to use cURL.
