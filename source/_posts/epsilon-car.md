---
title: Mini Program：Long-distance tracking smart car - Epsilon
date: 2018-07-19 18:11:03
categories: Study
tags:
- EE
toc: true
---

This is the product that was made in the Mini Program. Later, I also made a Gamepad for easily controlling. The Gamepad can emit the high-power infrared so the car can track the Gamepad in almost ten meters away. Compare with the other teams' product, the performance of Epsilon car is conspicuous. Most of students built their car with the ultrasonic tracking and as a result, available tracking range of their car is no more than 50cm! I am so proud of my Epsilon car 🙌

Though this Program is a team-work but my team members are not interesting at the EE. As a consequence, I built the car totally on my idea. It was a good experience to make my creative concept real. Especially worked on the cute Arduino mini!

<!--more-->

# Product Introduction

* Epsilon

<div align="center"> <img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010003404.png"/> <p align="center">fig. The overall appearence (Piano Theme) of Epsilon car</p> </div>

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010003314.png"/></div>
 
* Basic Function
  Epsilon car can automatically track the mobile infrared signal source within 6 meters and display the tracking distance and tracking time in real time.

* Additional Function
  * Ultrasonic ranging obstacle avoidance
  * Control the car with infrared remote or switch between remote control / tracking, totally two modes.
  * The car can change the turning radius. Remote acceleration and deceleration both are available.
  * Two robot dances built-in and you can customize the dance and store it.

* Opensource Repository
  [Click here to visit Epsilon Github!](https://github.com/zolars/Epsilon)

# Implementation of Functions

## Long-distance tracking infrared sources

> Innovative tracking methods are achieved with an independently built infrared receiver array.

It is well known that light travels in a straight line. So I made the isolation mask, with which found the location of the source accurately by judging the infrared rays. The identification of the tracking signal is achieved by modulating a specific band of infrared emitters. After two days of independent experiments, it was finally found that only three infrared probes were needed to achieve an effective detection angle of up to 270°.

Compared with the traditional ultrasonic or infrared probe tracking car, the Epsilon car can achieve true "tracking" and "obstacle avoidance" because of the long-distance infrared tracking. The biggest advantage of my group is that the effective range is significantly large and the tracking is not easily disturbed by obstacles. 

In the final show, the results of the Epsilon car is also impressive. **I hope this cheap, easy and feasible approach of infrared direction tracking can be used on transport, traffic or industry field in the future. This is a sort functional innovation which has more chances to explore.**

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010003655.png"/></div>

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(3).png"/></div>

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(4).png"/></div>



## Ultrasonic obstacle avoidance

In order to achieve the function of avoiding obstacles, I adopted the ultrasonic sensor with model of HC-SR04 whose detection distance is relatively close, ensures that the distance between the car and the obstacle is not too large or too small, and improves the accuracy of obstacle avoidance. By installing three ultrasonic sensors at a certain angle in the front of the car, the detection range is ensured which is 40cm. It can avoid obstacles accurately at the right angle.

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010003830.png"/></div>

To avoid unnecessary waste, improve the simple architecture, keep the products’ low cost, I do not adopt any other sensors.

# Appearance Design

## Preliminary Design

After reading some data and research, I decided to build the model using PVC board and abs board, rather than metal and wood. Furthermore, I found that a model with an appearance of a car or a robot has relatively small inner space, which is not a good choice for Epsilon car, which owned double-stacked board. Therefore, I chose a unique piano modeling which has higher space for the circuit design.

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010004125.png"/></div>

## Model Production

When finished the preparation work, I began to put the design into reality. I bought black and white PVC board and abs board from the online shopping website. Mixed the colors the model need and cut the board according to the blueprint, and then the structure of the piano was finally completed. 

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191010004250.png"/></div>


# Production Process Date

* The creative concept of the car was implemented with the opensource electronic platform Arduino.
* With Proteus, AutoCAD, Photoshop and other professional software, I established circuit simulation and product appearance design.
* Wrote, debuged program; and weld, installed circuits while improving code logic.
* Assembled the surface skeleton and decorated the details.
* Tested the whole process and the prepared of the acceptance documents.

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(1).png"/></div> 