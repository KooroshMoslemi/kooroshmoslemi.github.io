---
title: "Designing a Shooting Simulator Game"
date: 2021-11-11T00:00:00+00:00
description: "A shooting simulator game created for a school fair that uses a laser-equipped toy gun and an IP camera for scoring."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "Computer Vision"
  - "C++"
  - "OpenCV"
tags:
  - "Computer Vision"
  - "C++"
  - "OpenCV"
  - "Game Development"
hero: "shooting_view.jpg"
menu:
  sidebar:
    name: "Shooting Simulator Game"
    identifier: "shooting-simulator-game"
    weight: 70
---

<!-- {{< img src="https://drive.google.com/thumbnail?id=1ENNUF3DYnbB8v3upWc445OS61WfD3m-o&sz=w1024-h768" align="center" title="Advanced Line Follower Robot" >}} -->

Inspired by the annual science fair at my school, which encouraged students to explore new ideas and create innovative projects, my team and I decided to develop a game. Leveraging our experience from the [advanced line follower robot project](/posts/advanced-line-follower-robot/), we designed a shooting simulator game.

The setup involved embedding a laser into a toy gun and creating a target box with an archery target. An IP camera was placed inside the box to capture the laser's position on the target.

<div class="row">
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=1U-0PkbKLncO5alXdPPpAtNHmbEbBuLtj&sz=w640-h480" title="Game Setup 1" >}}
  </div>
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=1dp5jVJLQNb429zWc9-QoFLSaoC6Tbflo&sz=w640-h480" title="Game Setup 2" >}}
  </div>
</div>

<!-- {{< split 6 6 >}}
  {{< img src="https://drive.google.com/thumbnail?id=1U-0PkbKLncO5alXdPPpAtNHmbEbBuLtj&sz=w640-h480" title="Game Setup 1" >}}
---
  {{< img src="https://drive.google.com/thumbnail?id=1dp5jVJLQNb429zWc9-QoFLSaoC6Tbflo&sz=w640-h480" title="Game Setup 2" >}}
{{< /split >}} -->

The toy gun's trigger was connected to a small electronic board, allowing us to detect when a shot was fired. We could then calculate the user's accuracy based on the laser spot's position on the target.

Here is a video demonstration of the game:

{{< youtube 3c1-GARLbTw >}}
