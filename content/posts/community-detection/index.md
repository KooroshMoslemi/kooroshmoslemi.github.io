---
title: "Community Detection Using Genetic Algorithm and Cuckoo Search"
date: 2022-07-29T00:00:00+00:00
description: "An AI project on community detection in networks using Genetic Algorithm and Cuckoo Search, including locus-based representation and modularity as a fitness function."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "AI"
  - "Genetic Algorithm"
  - "Cuckoo Search"
tags:
  - "AI"
  - "Genetic Algorithm"
  - "Cuckoo Search"
  - "Community Detection"
hero: "graph.png"
menu:
  sidebar:
    name: "Community Detection"
    identifier: "community-detection"
    weight: 20
---

This project was an assignment for an AI course at the [Amirkabir University of Technology](https://aut.ac.ir/en), where the goal was to identify communities in a network using the [Genetic Algorithm](https://en.wikipedia.org/wiki/Genetic_algorithm) and [Cuckoo Search](https://en.wikipedia.org/wiki/Cuckoo_search). This post will focus on the problem-specific implementations rather than a detailed explanation of the algorithms themselves.

First, let's consider a sample input graph:

{{< img src="https://drive.google.com/thumbnail?id=1EIMeX0HL_mK1lmJXq2gk5iBwzXzWH-UA&sz=w640-h480" title="Sample Input Graph" align="center" >}}

### Finding Communities Using Genetic Algorithm

1.  **Genetic Representation and Fitness Function**:
    -   I used a locus-based representation for this problem, as illustrated below:
        {{< img src="https://drive.google.com/thumbnail?id=10Sl9PtVLBAG5ZQVKfU9Hs5exovN7IQAn&sz=w640-h480" title="Locus-based Representation" align="center" >}}
    -   The [modularity measure](https://en.wikipedia.org/wiki/Modularity_(networks)#Modularity) was used as the fitness function.

2.  **Selection**:
    -   [Roulette Wheel Selection](https://en.wikipedia.org/wiki/Selection_(genetic_algorithm)#Roulette_Wheel_Selection) was utilized for the selection step.

3.  **Crossover and Mutation**:
    -   A uniform crossover was used as follows:
        {{< img src="https://drive.google.com/thumbnail?id=1LHsOGQDDpAAvYr5uz2NmEFiJjPtZRakv&sz=w640-h480" title="Uniform Crossover" align="center" >}}
    -   The initial population was not entirely random. Instead, the process considered the network's existing connections to avoid uninteresting divisions of unconnected nodes. This approach restricts the search space and promotes faster convergence.

After 50 iterations with an initial population of 200 and a mutation rate of 0.4, the following communities were identified, achieving a fitness function value of 0.41978961209730353.

{{< img src="https://drive.google.com/thumbnail?id=1RvHEGvtlYhILmqm7vA_Hi7Ewmt1sd5Ab&sz=w640-h480" title="Genetic Algorithm Results" align="center" >}}

### Finding Communities Using Cuckoo Search

The Cuckoo Search algorithm is based on three idealized rules:
1.  Each cuckoo lays one egg at a time in a randomly chosen nest.
2.  The best nests with high-quality eggs are carried over to the next generation.
3.  The number of available host nests is fixed, and a host bird can discover an egg with a certain probability, at which point it can either discard the egg or abandon the nest and build a new one.

The pseudo-code for the algorithm is as follows:

{{< img src="https://drive.google.com/thumbnail?id=1I1abBTvf2YOQWALcVZI66Ez0tIor3xWb&sz=w640-h480" title="Cuckoo Search Pseudo-code" align="center" >}}

New solutions are generated using a Levy flight, a random walk where the step lengths follow a [Levy distribution](https://en.wikipedia.org/wiki/L%C3%A9vy_distribution). Since the original Cuckoo Search is designed for continuous spaces, the nest location updating and abandon operators were adapted for the discrete nature of community detection.

{{< img src="https://drive.google.com/thumbnail?id=1vhcfPRSYxDBnqlSGO7YfyoFyhNI8KU33&sz=w640-h480" title="Discrete Cuckoo Search 1" align="center" >}}
{{< img src="https://drive.google.com/thumbnail?id=1WliTZCWDbeYSJKO-YWf9HIXNODJLvBFm&sz=w640-h480" title="Discrete Cuckoo Search 2" align="center" >}}
{{< img src="https://drive.google.com/thumbnail?id=12g5ElS62JcG5nhZL3drtWrYC7b-4HFJC&sz=w640-h480" title="Discrete Cuckoo Search 3" align="center" >}}

After 30 iterations with an initial population of 200, the following communities were found, with a fitness function value of 0.4197896120973035.

{{< img src="https://drive.google.com/thumbnail?id=1JSssRiCdMHCX5_pe60ZFjtkor0gc--Dt&sz=w640-h480" title="Cuckoo Search Results" align="center" >}}

All parameter choices and the source code are available in this [GitHub repository](https://github.com/KooroshMoslemi/CommunityDetection).

### References:
1.  Pizzuti Clara. GA-Net: A Genetic Algorithm for Community Detection in Social Networks.
2.  Xin-She Yang and Suash Deb. Cuckoo Search via Lévy flights.
3.  Xu Zhou, Yanheng Liu and Bin Li. A multi-objective discrete cuckoo search algorithm with local search for community detection in complex networks.
