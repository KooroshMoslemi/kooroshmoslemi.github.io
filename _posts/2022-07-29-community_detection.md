---
layout: post
title: Community Detection Using Genetic Algorithm and Cuckoo Search
categories: [AI,Genetic Algorithm,Cuckoo Search]
---
                                               
This project was one of my assignments for an AI course at [AUT](https://aut.ac.ir/en). In this project, one had to find communities in a network using the [Genetic Algorithm](https://en.wikipedia.org/wiki/Genetic_algorithm) and [Cuckoo Search](https://en.wikipedia.org/wiki/Cuckoo_search). I will mainly describe steps specific to this problem rather than explaining the algorithms.

First things first, let's look at a sample input graph:
<img src="https://drive.google.com/thumbnail?id=1EIMeX0HL_mK1lmJXq2gk5iBwzXzWH-UA&sz=w640-h480"/>  

### Finding Communities Using Genetic Algorithm:

1. Genetic Representation and Fitness Function:
    - I used a locus-based representation for this problem which is illustrated as follows:
    <img src="https://drive.google.com/thumbnail?id=10Sl9PtVLBAG5ZQVKfU9Hs5exovN7IQAn&sz=w640-h480"/>
    - Moreover, I used the [modularity measure](https://en.wikipedia.org/wiki/Modularity_(networks)#Modularity) as a fitness function.
2. Selection:
    - I utilized the [Roulette Wheel Selection](https://en.wikipedia.org/wiki/Selection_(genetic_algorithm)#Roulette_Wheel_Selection) for the selection step. 
3. Crossover and Mutation:
    - A uniform crossover was used as follows:
    <img src="https://drive.google.com/thumbnail?id=1LHsOGQDDpAAvYr5uz2NmEFiJjPtZRakv&sz=w640-h480"/>
    - It is worth mentioning that the initial population is not completely random. Instead, the process considers the original network's connections, meaning that individuals avoid uninteresting divisions containing unconnected nodes. In this way, the search space is restricted, and it is likely to converge faster. We call these individuals safe. As a result, given two safe parents, a safe child is generated in a uniform crossover. Furthermore, in the mutation step, we make sure safety is regarded. 


Finally, after 50 iterations with 200 initial populations, the following communities were found. In this division, the value of the fitness function is 0.41978961209730353, and the mutation rate is 0.4.
<img src="https://drive.google.com/thumbnail?id=1RvHEGvtlYhILmqm7vA_Hi7Ewmt1sd5Ab&sz=w640-h480"/>


### Finding Communities Using Cuckoo Search:

Cuckoo Search is based on three idealized rules:
1. Each cuckoo lays one egg at a time and dumps its egg in a randomly chosen nest;
2. The best nests with high-quality eggs will carry over to the next generation;
3. The number of available host nests is fixed, and the egg laid by a cuckoo is discovered by the host bird with a      probability between 0 and 1. In this case, the host bird can throw the egg away and abandon the nest, and build a completely new nest.

The pseudo-code is as follows:
<img src="https://drive.google.com/thumbnail?id=1I1abBTvf2YOQWALcVZI66Ez0tIor3xWb&sz=w640-h480"/>

Generation of new solutions is performed using a Levy flight, which is a random walk in which the step lengths have a [Levy distribution](https://en.wikipedia.org/wiki/L%C3%A9vy_distribution). 

The original Cuckoo Search(CS) is for continuous space. Thus, we need to change the nest location updating strategy and the abandon operator in discrete form because of the discrete nature of community detection. Here is one solution:
<img src="https://drive.google.com/thumbnail?id=1vhcfPRSYxDBnqlSGO7YfyoFyhNI8KU33&sz=w640-h480"/>
<img src="https://drive.google.com/thumbnail?id=1WliTZCWDbeYSJKO-YWf9HIXNODJLvBFm&sz=w640-h480"/>

According to [this](https://www.researchgate.net/publication/297674203_A_multi-objective_discrete_cuckoo_search_algorithm_with_local_search_for_community_detection_in_complex_networks) paper:
<img src="https://drive.google.com/thumbnail?id=12g5ElS62JcG5nhZL3drtWrYC7b-4HFJC&sz=w640-h480"/>

After 30 iterations with 200 initial populations, the following communities were found. In this division, the value of the fitness function is 0.4197896120973035.
<img src="https://drive.google.com/thumbnail?id=1JSssRiCdMHCX5_pe60ZFjtkor0gc--Dt&sz=w640-h480"/>

All of the parameter choices and the source code are available in [this](https://github.com/KooroshMoslemi/CommunityDetection) repository.

### References:

1. Pizzuti Clara. GA-Net: A Genetic Algorithm for Community Detection in Social Networks.
2. Xin-She Yang and Suash Deb. Cuckoo Search via Lévy flights.
3. Xu Zhou, Yanheng Liu and Bin Li. A multi-objective discrete cuckoo search algorithm with local search for community detection in complex networks.











