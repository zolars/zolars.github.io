---
title: 移动端利用 SSH 进行远程开发
date: 2018-03-01 11:22:03
categories: Study
tags:
- CS
toc: true
---

## 摘要

随着 Linux Server 在企业中的流行，如何管理 Linux 服务器是网络人员面临的关键任务。 作为一种实用的安全标准，SSH 协议可以在两台计算机之间提供安全通信。 本文研究将 Linux Server 放在虚拟机下，并使用特定软件在移动端远程管理 Linux Server，这解决了移动平台（iOS，Android）远程管理 Linux 服务器的问题。

<!--more-->

## Linux 服务器

Linux 是免费的操作系统，提供从可用性到安全性的许多优势。对于大型远程服务器的搭建，Linux 操作系统是最好的选择。以下介绍了 Linux 提供的一些优势。

1. 低成本
   Linux 的主要优点是开源免费，而 Windows Server 等其他操作系统一般需要支付高额费用才能获得。实际上，Linux 在使用和安装方面没有任何严格的许可限制。任何具有编程知识的人都可以轻松地操纵 Linux 源代码，从而个性化的增强他们的使用体验。

2. 硬件优势
   Linux 适合内存或处理能力有限的计算机，可以将这些性能有限的机型制作成大型原创服务器，例如备份服务器或文件服务器。几乎没有 RAM 内存的计算机也可以流畅运行 Linux。

3. 更好的安全性
   与 Windows 操作系统相比，Linux 另一个巨大的优势是它非常安全。Windows 操作系统总是面临大量的安全威胁，但是，Linux 系统下的间谍软件，恶意软件和病毒数量很少。

4. 广泛的软件选项
   当您想要执行特定任务时，Linux 中提供了许多的可选软件与便捷的安装。鉴于开源程序员和用户不断贡献新的应用程序，Linux上的软件产品通常具有更多功能，并且具有更好的可用性。

## VS Code Remote 插件应用分析

谈及 SSH 的远程移动开发，先从 Windows 上的远程开发工具的分析开始。目前微软的 Visual Studio Code 团队开发了一种编辑器内置插件的方案。

> SSH 扩展允许用户连接到任何远程计算机，虚拟机或容器（Docker）上的远程文件夹与正在运行的 SSH 服务器，并充分利用 Visual Studio Code 的插件。连接到服务器后，用户可以与远程文件系统上的任何位置的文件和文件夹进行交互。这使 VS Code 能够提供本地质量的开发体验 - 包括完整的 IntelliSense，代码导航，项目管理和调试 - 无论您的代码在何处托管。由于扩展程序直接在远程计算机上运行，因此本地计算机上不需要任何工程源代码。
>
> ![](https://raw.githubusercontent.com/zolars/pic-bed/master/20191011004136.png)

我使用 VS Code Remote 连接远程服务器的实验取得了意料之中的成功。原则上说，这个插件的功能是利用 SSH 开启远程机中的 VS Code 平台并进行操纵，功能完善，快捷。缺点是只能在桌面平台使用，没有移动端的相似产品。



## Termius 全平台 APP 分析

在接触了全功能的 SSH 开发平台之后，我关注了一个简单的 SSH 平台。

Termius 只提供了命令行与 SFTP 接口等。在功能上远不如 VS Code Remote 完善，但是借助 Vim 和 Shell 还是可以实现部分简单的开发。Termius 的突出优势是其使用 Electron 框架实现了 iOS，Android，Windows，Mac 全平台化。

实际的使用场景大多是在通勤的道路上处理突发需求。在最近的工程项目上，我接入了实验室的高性能主机制作服务器。服务器经常因为各种各样的原因宕机，所以我经常在没有 PC 的条件下处理需求。Termius 给我提供的便利主要在于 SFTP 的内置，使我能够使用 iPad 配合简单的编辑器进行代码和指令的微调。虽然很难处理大型任务，但是状态查看，重启与应急处理是足够了。

如果在 Termius 的基础上开发 SSH APP，最佳的效果是能够内置一个性能强大的移动编辑器，能够应对撤销，复制粘贴，代码格式化等需求。

## 利用 Electron 将 VS Code Remote 的相关功能移植到移动平台的前景

GitHub ELectron（简称Electron）允许开发者仅仅使用HTML、CSS和JavaScript就可以构建桌面应用。实际上正如Apache Cordova（也叫PhoneGap）允许只用HTML、CSS和JS来构建移动应用，Electron为跨平台开发提供新可能。

> Electron最初是用于开发新编辑器Atom的技术，在2013年由Github工程师赵成开发。一开始这项技术被称为Atom Shell，后来改称Electron。虽然当时已经有类似技术，Electron一经问世就被大量开发者关注。实际上早在2008年，使用HTML、CSS和JavaScript开发桌面应用的Adobe AIR就已经发布，替代了ActionScript。所以说Electron不是将web技术用于浏览器之外的开山鼻祖。

这项新的技术一经问世就受到广泛关注，VS Code 也是在 Electron 框架下开发出来的。那么是否能够将 VS Code 的Electron 源码移植到 iOS 和 Android 呢？答案当然是肯定的。只不过目前 VS Code 的开源 Road Map 中还没有涉及到这个方面。在微软 Build 2019 开发者大会上，微软宣布了 Web 版本的 VS Code - Visual Studio Online。

除了官方预告之外，[coder.com](<https://coder.com/enterprise>) 已经开源商业化，实现了 VS Code Online 的大多数需求，并提出了崭新的商业化模式。

![coder.com的服务](https://raw.githubusercontent.com/zolars/pic-bed/master/20191011004031.png)

如上图，coder.com 切入的用户痛点是：简易的环境配置，无缝的团队合作，便于中层管理与审核等。针对中小型企业，所有代码完全云端管理，所有工程师都能远程开发，既节省了人力成本，又方便协同合作。这也是现阶段依托于 SSH 远程应用的最佳体现。

## 总结

SSH 作为一种高性能的远程连接协议，功能强大而简洁，可拓展性高。充分利用 SSH 的优点来实现云端互联，将远程主机这个并不复杂的概念普及到大众中去，最大化的发挥智能手机和 PC 的共同协作，让每一块 GPU 都不空转，将是这个领域未来的目标。设想未来，越来越多的可用设备将会实现云端共享，使大规模并行式计算成为可能，以此人工智能的开发又将上一个新的台阶；越来越多的用户了解 SSH（或者远程主机） 的优势，可能不会购置昂贵的台式电脑，而去租用性价比更高的云主机，以此节省硬件浪费，促进环保。而这一切，都依托于 SSH APP 的开发，需要我们发挥足够的创造力，去拓展一片尚未开垦的良田，将一种技术，用好用活。

