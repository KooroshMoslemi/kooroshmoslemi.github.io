---
title: "Advanced Line Follower Robot"
date: 2021-11-10T00:00:00+00:00
description: "An advanced line follower robot that uses a camera and OpenCV for image processing to detect lines and shapes of different colors."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "Robotics"
  - "C++"
  - "OpenCV"
  - "AVR"
tags:
  - "Robotics"
  - "C++"
  - "OpenCV"
  - "AVR"
hero: "tanki.png"
menu:
  sidebar:
    name: "Advanced Line Follower Robot"
    identifier: "advanced-line-follower-robot"
    weight: 10
---

{{< img src="https://drive.google.com/thumbnail?id=1x8KBGWNxjee1NCjo61HL6qvCS4usiH6j&sz=w1024-h768" align="center" title="Advanced Line Follower Robot" >}}

Building upon our experience with the [simple line follower robot](/posts/simple-line-follower-robot/), my team and I decided to develop a more advanced version with enhanced capabilities. This iteration replaced the basic IR sensors with a camera, enabling the robot to perform image processing to identify and follow lines and shapes of various colors.

Here is a video of the robot:

{{< youtube WU4G3W5LuWQ >}}

The image processing pipeline was as follows:

- The video stream from the camera was sent to a PC via a wired connection. We also successfully tested using an IP camera over a local network for real-time video capture.
- We used OpenCV in C++ to process the incoming frames.
- Control commands were then sent from the PC to the robot using a USB to TTL module. We also experimented with HMT-HMR modules for wireless communication.

This project was our first foray into computer vision, and we accomplished our goals without using any machine learning or deep learning techniques. We developed robust, custom color filters and were able to detect shapes based on hand-crafted features like the number of corners and angles between lines.

Here is another video showcasing the shape detection:

{{< youtube 7ZfZ9vcfb7g >}}

Here are some images of the project:

<div class="row">
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=196zBOHztwLeHswAGUZ79sPUay_HjCVrY&sz=w1024-h768" align="center" title="Color Detection" >}}
  </div>
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=1fbRpHqrfq94zltIqox7gSIssUgD3LZOe&sz=w1024-h768" align="center" title="Shape Detection" >}}
  </div>
</div>
