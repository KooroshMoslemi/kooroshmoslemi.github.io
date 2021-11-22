---
layout: post
title: Designing a Shooting Simulator Game
categories: [Computer Vision, C++, OpenCV]
---

<img src="https://drive.google.com/thumbnail?id=1ENNUF3DYnbB8v3upWc445OS61WfD3m-o&sz=w640-h480"/>                                                

There was an annual fair in my school in which all students could present their projects. It was a great motivation to explore new ideas and innovate cool stuff!

As we learned a lot from our [advanced line follower robot](../advanced-line-follower-robot), we decided to use our experience in that project and design a game.
Our idea was to create a shooting simulator game. So, we started by embedding a laser in a toy gun. We then designed a box with an archery target on one side. We also put an IP camera inside the box to capture video and process it with pc. 

<div class="row">
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=1U-0PkbKLncO5alXdPPpAtNHmbEbBuLtj&sz=w640-h480"/>
  </div>
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=1dp5jVJLQNb429zWc9-QoFLSaoC6Tbflo&sz=w640-h480"/>
  </div>
</div>

The trigger in our toy gun was connected to a small electronic board. So, whenever a user was trying to shoot, we could score his accuracy based on the position of the laser spot.

Here is a video that demonstrates this:
<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/3c1-GARLbTw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>







