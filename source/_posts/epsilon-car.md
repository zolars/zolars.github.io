---
title: 2018小学期：长距离定向跟踪小车-Epsilon
date: 2018-07-19 18:11:03
categories: Study
tags:
- Arduino
- BUPT
toc: true
---

> 这是小学期做出来的产品啦，后来还做了一个操控用手柄————总之都是我一个人搭建起来的，在这里放一下。

<!--more-->

## 产品介绍

* Epsilon
 
<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(2).png"/></div>
 
<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(11).jpeg"/></div>
 
* 基础功能
  Epsilon小车能够自动对六米范围内的移动红外信号发射源进行准确跟踪，并能够实时显示跟踪距离和跟踪时间。
 
<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(3).jpeg"/></div>
 
* 附加功能
  - 超声波测距避障
  - 红外遥控小车行进，可切换遥控 / 追踪两种模式。
  - 小车可以改变转弯半径以及加减速。
  - 内置两段机器人舞蹈，可以自定义舞蹈并存储。

* 关注 / 联系作者
  [Epsilon Github](https://github.com/zolars/Epsilon)


## 制作流程
* 利用开源电子原型平台Arduino完成了该小车的创意概念。
* 使用Proteus，AutoCAD，Photoshop等专业软件进行电路仿真以及产品外观的设计。
* 搭建、调试电路并进行电路的焊接和安装，同时完善代码逻辑。
* 拼装外观骨架与装饰细节的实现。
* 整机流程测试并进行验收文件的准备。

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(1).png"/></div>

## 主要功能实现

### 红外发射源定点追踪

> 利用自主搭建的红外接收器阵列，实现了创新的追踪方式。

众所周知，光沿直线传播。所以我们自制了隔离遮罩，通过判断红外线的来向精确的找到发射源的位置。借助调制特定波段的红外线发射器来实现追踪信号的识别。经过两天的自主实验，最终发现只需要三个红外探头就可完成高达270°的有效探测角度。

对比传统的超声波或者红外探头的追踪小车，Epsilon小车因为采用了红外定点追踪，才能实现真正意义上的“追踪”与“避障”。我组最大的优势为：有效范围大，且追踪不易受障碍物的干扰。

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(3).png"/></div>

之所以选用红外定位：红外线传播距离远，有效范围大；它不能通过遮挡物，抗干扰能力强；而红外发光二极管安装便利，体积小，成本低。

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(4).png"/></div>

### 超声波测距避障

> 使用超声波传感器来实现躲避中等体积的障碍物。

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(5).png"/></div>

<p align="center">通过声波的反射和声速计算出和物体的距离</p>

### 红外遥控小车

> 通过特定波段的红外线的调制解调来给小车下达指令。

类似传统遥控器的实现原理，通过Arduino中IRremote库来编码解码红外信号。

## 外观概念描述

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(6).png"/></div>

## 电路仿真图

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/Epsilon%20(7).png"/></div>

## 结语

即使我们的Epsilon追踪小车已经实现了诸多功能，仍它是一个尚未成熟的产品。我们会在接下来的两个月持续的完善它，期待在09/25的最终验收中，拿出更全面、更实用、更优秀的作品。