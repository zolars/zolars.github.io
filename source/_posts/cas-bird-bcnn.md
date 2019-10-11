---
title: Fine-grained bird classification experiment with the BCNN
date: 2019-05-08 15:41:28
categories: Study
tags:
- CV
toc: true
mathjax: true
---

## Paper's Principle

The experiment is based on the principle of fine-grained recognition in **Bilinear CNN Models for Fine-grained Visual Recognition [[1]](#1)**. Using networks initialized from the ImageNet dataset followed by domain specific fine-tuning the author of this paper obtain 84.1% accuracy of the CUB-200-2011 dataset requiring only category labels at training time. 

<img src="https://raw.githubusercontent.com/zolars/pic-bed/master/20190719090610.jpg"/>

<!--more-->

Its key algroithm is as follows:

> It consists of two feature extractors based on CNNs whose outputs are multiplied using **the outer product** at each location of the image and pooled across locations to obtain an image descriptor. **The outer product** captures pairwise correlations between the feature channels and can model part-feature interactions.
>
> Moreover, the architecture can be easily trained end-to-end leading to significant improvements in performance.
> 
> Since our model is linear in the outputs of two CNNs we call our approach bilinear CNNs.

## Experiment Approach

### Reproducing

With the PyTorch framework, I reproduce the fine-grained classification accuracy, the author's achievement, on CUB200-2011 dataset.

The format of the training images is three-channel RGB 448*448, and the total number of features is 512.

The model structure of BCNN is as follows:

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

## Dataset Introduction

The Waterbirds dataset includes 164 different sorts of waterbirds. And each category contains 100 pictures for training and 10 to 400 pictures for testing. After image enhancement and filtering, a total of 16,400 train data and 11,061 test data were included. The size of this dataset is 15.3GB.

The formats of most of picture files are three-channel RGB images (jpg), and the others are RGBA format (png, tif). I pretreated all the photos to simple RGB format before starting training.

Image enhancement was been used to augment the amount of training data of some of these categories. So some features may be interfered when implementing training. In addition, the test dataset of some categories is scarce, resulting in the accuracy of the test will be lower than the actual level.

## Hyperparameters

For pre-training, the batch_size is 64; the epoch num is 55; And the weight decay is 1e-8.

For fine-turn, the batch_size is 32; The epoch num is 25; And the weight decay is 1e-5.

## Result Analysis

Reproducing on CUB200-2011 dataset, the experiment obtained 91% accuracy for training and 84.1% accuracy for testing, which totally matches the results given by the paper. It costs almost 4h for the full training.

On the new waterbirds dataset, the experiment obtained 96% accuracy for training and 87.7% accuracy for testing. The accuracy for testing was slightly lower than the target, 90%. The complete training and testing takes about 10 hours.

### Advantages

1. The recognition accuracy of the model is significantly higher than traditional approaches such as FC-CNN, FV-CNN. The fine-grained classification method can be used to distinct the waterbirds' feet, ticks or textures.
2. The model establishes end-to-end training, with low cost, high training performance and fast speed.
3. Unsupervised training without the use of target detection tags to aid training. There are little requirements for the training set.

### Issues

1. As the paper pointed out, the model will confuse some categories. For birds whose main difference is in wingspan, habitat or sound, the model is difficult to make accurate classification. Other common confusions appear due to visually similarity. For example, the similar appearances of greater scaup and Tufted Duck.
2. Especially among the waterbirds, the different sorts of females are extremely hard to distinct than different sorts males. We take the eurasian green-winged teal and the baikal teal as examples. As the following figure, the male eurasian green-winged teal and the baikal teal can be easily distinguished. However, the difference in texture characteristics is not obvious between female birds. These inconspicuous differences affect the model's accuracy, depending on the proportion of female waterbirds' data in the dataset.

<div align="center"><img src="https://raw.githubusercontent.com/zolars/pic-bed/master/20190719090609.jpg" width="50%"/></div>

<p align="center">figure1. the male and female eurasian green-winged teal (Anas crecca)</p>

<div align="center"><img src="https://raw.githubusercontent.com/zolars/pic-bed/master/20190719090608.jpg" width="50%"/></div>

<p align="center">figure2. the male and female baikal teal (Sibirionetta formosa)</p>

3. Lack on typical feature or the scarce data quantity makes the judgment of the model difficult. Such as the misrecognition between Phalacrocorax carbo and Phalacrocorax pelagicus.

## Optimization Target

1. Noticing that deploying the model costs too many time, the next goal is to realize the feasible and high-quality method to reduce time cost on rebuilding the model. When using the model to identify birds, can the model instance be kept in memory once completely loaded?
2. For the second issue above, I suppose to classify the male and female data. The male birds and female birds are also considered as two types during training. Extracting their feature points separately will significantly improve the recognition accuracy of the model.
3. Call for additional size of dataset in specific categories. <div id='1'></div>

> ## Reference
>
> 1. Lin, Tsung-Yu, Aruni RoyChowdhury, and Subhransu Maji. "Bilinear cnn models for fine-grained visual recognition." Proceedings of the IEEE international conference on computer vision. 2015.