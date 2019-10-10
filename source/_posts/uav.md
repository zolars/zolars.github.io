---
title: UAV-Aided Time-Sensitive IoT Networks
date: 2019-09-10 16:51:02
categories: Study
tags:
- EE
- RL
toc: true
mathjax: true
---

I just finished the paper with Nanxin. It's a great cooperation for both of us, I guess. For me, I learned much about the UAV and combinatorial optimization by talking with his concept; For him, he found me, ~~just a good programmer~~, to establish simulation with basic algorithm or RL in CS field. 

<!--more-->

This simulation is such as creatingg a new environment for [OpenAI gym](https://gym.openai.com/). As we all know, gym is a toolkit for developing and comparing reinforcement learning algorithms and there are many default exvironments such as Atari games or CartPole etc.  For our work we had to design different algorithms and evaluate their performance so as a consequence, I designed a common environment to emulate our UAV model. Addition of the code-reuse is indispensable to reduce my workloads.

With this environment, I can easily input the starting point (coordinates) and end point (sensors' ID) to emulate the UAV's flights. The UAV will automatically judge whether the energy is sufficient or not. If the energy is not enough to support the next flight, UAV will fly home and refill the energy. I also modelled the 3D sensors range detectable. 

Due to the preparation above, I can simplify the complex process of UAV's flight. We seen the tour as targets' sequences. As a result, the 3D sensitive-route-plan question is simplified to a sequences question. Then, the Q-Learning and DQN are available. Input is the current observations and output is the next target among sensors.

What's more, I am still fresh in the field of combinatorial optimization. If the environment is less comprehensive, the problem seems like to be appropriate for the classical optimization algorithms such as DP. But this is the real world and the study on real UAV rather than the toy model. Remind me to learn more about the "REAL" combinatorial optimization in order to deal with really complex situations such as the traffic jam during the rush hours 🚗🚗🚗🚗🚗🚗🚗.



