---
layout: post
title: Advanced Line Follower Robot
categories: [Robotics, C++, OpenCV, AVR]
---

<img src="https://drive.google.com/thumbnail?id=1x8KBGWNxjee1NCjo61HL6qvCS4usiH6j&sz=w640-h480"/>

A year after designing our [simple line follower robot](../line-follower-robot), we decided to go further and add more complex features!
We started with replacing IR sensors with a camera. We also changed the design altogether. We wanted our robot to differentiate between lines and shapes of different colors. So we started to learn image processing!
Here is what we build:

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/WU4G3W5LuWQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

The overall procedure is described as follows :

- First, we sent the camera stream through a wired connection to our pc and then processed the image with OpenCV in C++. We also tested an IP camera and captured frames through a local network that worked in real-time.
- After processing the image, we sent proper controlling commands to the robot with a USB to TTL module. We also experimented with HMT-HMR modules.

As This project was our first experience with computer vision, we did not use any ML/DL techniques.
We created robust and custom color filters, and we were able to detect shapes through hand-crafted features like the number of corners and angles between lines!

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/7ZfZ9vcfb7g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

<div class="row">
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=1fbRpHqrfq94zltIqox7gSIssUgD3LZOe&sz=w640-h480"/>
  </div>
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=196zBOHztwLeHswAGUZ79sPUay_HjCVrY&sz=w640-h480"/>
  </div>
</div>





