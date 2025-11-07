---
title: "Detecting Iranian Paper Money to Help People With Visual Disabilities"
date: 2021-11-12T00:00:00+00:00
description: "A deep learning project to detect Iranian paper money for visually impaired individuals, using TensorFlow Lite and transfer learning on MobileNet."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "Edge ML"
  - "TensorFlow Lite"
  - "Image Classification"
tags:
  - "Deep Learning"
  - "Machine Learning"
  - "TensorFlow Lite"
  - "MobileNet"
  - "Android"
hero: "tflite_android_banknote.png"
menu:
  sidebar:
    name: "Currency Detection"
    identifier: "currency-detection"
    weight: 30
---

This project, undertaken just before I began my university studies, was my first application of deep learning to solve a real-world problem. The inspiration came from Microsoft's Seeing AI app, which offers a range of tools for visually impaired individuals. One of its standout features is the ability to identify currency bills, a functionality I aimed to replicate for Iranian currency, which was not supported by the original app.

A significant challenge was the lack of an existing dataset. I dedicated a month to collecting and curating a suitable dataset of Iranian banknotes. During this time, I researched various approaches and decided to use transfer learning with the MobileNet architecture, as the goal was to deploy the model on an Android device. TensorFlow Lite provided the ideal framework for on-device inference.

After several weeks of development, I produced the following result:

{{< youtube 0x0-5DCLBB4 >}}

Although I was still new to many of the intricate details of the model, this project was a tremendous learning experience. The most remarkable aspect for me was the transition from hand-crafted features, which I had used in my [advanced line follower robot](/posts/advanced-line-follower-robot/) and [shooting simulator game](/posts/shooting-simulator-game/) projects, to a deep learning approach where the model learned the features automatically.

This project ignited my passion for machine learning and deep learning, motivating me to delve deeper into this fascinating field.
