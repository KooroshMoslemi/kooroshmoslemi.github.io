---
layout: post
title: Detecting Iranian Paper Money to Help People With Visual Disabilities
categories: [Edge ML,TensorFlow Lite, Image Classification]
---

This project was the last one before I entered university. I like it because it was the first time that I solved a problem using deep learning. 
The idea came to me when I first saw [the Seeing AI app from Microsoft](https://www.microsoft.com/en-us/ai/seeing-ai).

It had many features that could help a person with visual disabilities and ease their life. One interesting feature was to identify currency bills when paying with cash. I tried to implement this for the people of my country because the original app only supported hard foreign cash.

As there was no dataset to train with, I spent one month collecting a good one, and meanwhile, I was studying possible approaches to this kind of problem. 
I decided to use transfer learning on MobileNet because I wanted to run the model on an android device. I realized TensorFlow has an excellent framework for on-device inference. So, I started to explore the documentation, and after a couple of weeks, I came up with this result:

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/0x0-5DCLBB4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

Even though I did not fully understand each tiny detail in the model that I trained, I still learned a lot of things that I did not know before starting the project. For me, the most impressive part of this project was the fact I did not use any hand-crafted feature similar to what I used in my [advanced line follower robot](../advanced-line-follower-robot) and [shooting simulator game](../shooting-simulator-game).

I knew there was still a lot more to explore in this field, and I had barely scratched the surface of it!

This project later motivated me to learn more about machine learning and deep learning.







