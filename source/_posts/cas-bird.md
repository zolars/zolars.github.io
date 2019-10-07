---
title: BCNN实现的细粒度鸟类分类实验报告
thumbnail: https://raw.githubusercontent.com/zolars/typora-user-images/master/20190719090608.jpg
date: 2019-05-08 15:41:28
categories: Coding
tags:
- CV
- CAS
- fine-grain
- python
toc: true
mathjax: true
---

## 算法原理

实验基于论文 Bilinear CNN Models for Fine-grained Visual Recognition (2017) 中的细粒度识别原理实现。论文作者使用从 ImageNet 数据集初始化的网络，然后进行特定于域的微调。他们获得了 CUB200-2011 数据集的84.1％准确度，而且在训练时仅需要提供类别标签。

<!--more-->

<img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/20190719090610.jpg"/>

> It consists of two feature extractors based on CNNs whose outputs are multiplied using **the outer product** at each location of the image and pooled across locations to obtain an image descriptor. **The outer product** captures pairwise correlations between the feature channels and can model part-feature interactions.
>
> 它由两个基于CNN的特征提取器组成，其输出在图像的每个位置使用**外积**相乘，并跨位置合并以获得图像描述符。 **外积**捕获特征通道之间的成对相关性，并可以模拟部件特征交互。
>
> Moreover, the architecture can be easily trained end-to-end leading to significant improvements in performance.
>
> 此外，该架构可以轻松地端到端地进行训练，从而显着提高性能。
>
> Since our model is linear in the outputs of two CNNs we call our approach bilinear CNNs.
>
> 由于我们的模型在两个CNN的输出中是线性的，我们称之为双线性CNN。

## 实验方法

### 复现

使用 PyTorch 框架复现论文作者在 CUB200-2011 数据集上实现的细粒度分类。

训练用图像的格式为三通道RGB 448*448，总特征数为512.

使用的 BCNN 的模型结构如下：

```
(module): BCNN(
    (features): Sequential(
      (0): Conv2d(3, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (1): ReLU(inplace)
      (2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (3): ReLU(inplace)
      (4): MaxPool2d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
      (5): Conv2d(64, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (6): ReLU(inplace)
      (7): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (8): ReLU(inplace)
      (9): MaxPool2d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
      (10): Conv2d(128, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (11): ReLU(inplace)
      (12): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (13): ReLU(inplace)
      (14): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (15): ReLU(inplace)
      (16): MaxPool2d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
      (17): Conv2d(256, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (18): ReLU(inplace)
      (19): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (20): ReLU(inplace)
      (21): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (22): ReLU(inplace)
      (23): MaxPool2d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
      (24): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (25): ReLU(inplace)
      (26): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (27): ReLU(inplace)
      (28): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
      (29): ReLU(inplace)
    )
    (fc): Linear(in_features=262144, out_features=200, bias=True)
  )
```

## 数据集介绍

水鸟数据集中包含164种不同的水鸟，每一类包含100张训练数据，10-400张不等的测试数据。图像增强之后一共包含16400张训练用数据，11061张测试用数据。数据集大小15.3GB。

大部分照片数据格式为三通道RGB图片(jpg格式)，也有部分RGBA格式 (png, tif) 的照片。所以在开始训练之前将所有照片强制转换为RGB格式。

其中有部分类别采用了数据增强来扩充训练数据的数量，因此在实现训练时可能会遗漏部分特征。除此之外部分类别的测试集太小，导致测试的准确率也会比实际水平偏低。

## 实验参数

预训练时的batch_size为64，迭代次数为55，权值衰减为1e-8。

Fine-turn时的batch_size为32，迭代次数为25，权值衰减为1e-5。

## 结果分析

在 CUB200-2011 数据集上复现时，训练准确率达到91%，测试准确率达到84.1%，与论文作者的实验结果相符。完整训练加测试用时约4h。

在新的水鸟数据集上实验时，训练准确率达到96%，测试准确率达到87.7%，测试准确率稍低于预期的90%。完整训练加测试用时约10h。

### 方法优点

1. 模型的识别准确率显著高于传统方法（如FC-CNN，FV-CNN）。能够采用细粒度分类方法对绝大部分水鸟的足，喙与纹理进行识别。
2. 模型采用端到端训练，训练性能高，训练速度快。
3. 是无监督训练，无需使用目标检测标签来辅助训练。对训练集的要求小。

### 存在问题

1. 如同论文中指出的，模型会混淆部分分类。对于主要差异在于翼展，栖息地和声音的鸟类，该模型很难做出准确判断。其他常见的混淆类也在视觉上相似，例如凤头潜鸭Aythya fuligula与斑背潜鸭Aythya marila等。
2. 在水鸟这个特殊的种类中，有部分雌性的差异远不如雄性那么明显。例如绿翅鸭Anas crecca与花脸鸭Anas formosa。如下图明显可以看出，虽然可以轻松分辨雄性的绿翅鸭和花脸鸭，但是对于雌性，它们的纹理特征区别十分的不明显。这些不明显的区别会对训练与测试准确率造成影响，取决于数据集中雌性图片的占比。

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/20190719090609.jpg" width="50%"/></div>

<p align="center">figure1. 雌雄绿翅鸭的特征</p>

<div align="center"><img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/20190719090608.jpg" width="50%"/></div>

<p align="center">figure2. 雌雄花脸鸭的特征</p>

1. 部分分类的数据集缺乏典型性或数量太少，例如普通鸬鹚与海鸬鹚。这会造成模型的判断困难。

## 优化方案设想

1. 在使用模型识别鸟类时，将模型持续的载入内存，可以节省搭建模型的时间消耗。
2. 对于存在问题中第二项，我认为可以将雌雄数据做一定的分类。在训练的时候，也将雄鸟和雌鸟视作两类。分别去提取它们的特征点，将会显著的提升模型的识别成功率。
3. 适当的增加数据集的数量，填补某些分类数据量太少的问题。

> ## Reference
>
> 1. Lin T Y, RoyChowdhury A, Maji S. Bilinear cnn models for fine-grained visual recognition[C]//Proceedings of the IEEE international conference on computer vision. 2015: 1449-1457.