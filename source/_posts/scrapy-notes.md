---
title: scrapy Learning Notes
date: 2016-10-23 01:14:22
categories: Study
tags:
- CS
toc: true
---

# 爬虫学习笔记
自己学习中的一些理解，同时也是面向新手的介绍（当然你得稍微了解一点 Python 的基础语法吧）。有很多地方的思考还不够深入，这一篇文章也会随着自己的学习慢慢充实。

<!--more-->

## 目的
现今互联网信息爆炸，每个网址上都有成千上万的文字、图片、超链接；自然也存在很多垃圾信息，诸如恶意投放的广告、繁杂的页面装饰等。制作一个干净清爽的阅读页面——检索页面信息，只存留有价值的图文而剔除其他——就需要借助网页爬虫了。（当然使用官方 app 或者阅读模式也是很好的选择，暂且不谈）

想要检索大量页面，寻找有价值的信息也需要爬虫的帮助。实际上我们平时所使用的搜索引擎就源自强大而高效率的爬虫。

听上去很吸引人，那么我们来试图制作自己的爬虫。

## 实现原理
要理解了爬虫的实现原理，先要理解网页是什么。

> 网页是一个适用于万维网和网页浏览器的文件，它存放在世界某个角落的某一部或一组计算机中，而这部计算机必须是与互联网相连。网页经由网址（URL）来识别与访问，当我们在网页浏览器输入网址后，经过一段复杂而又快速的程序，网页文件会被传送到用户家的计算机，然后再通过浏览器解释网页的内容，再展示给用户。[网页 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81)  

缩句，得：

> **网页**是一个适用于万维网和网页浏览器的**文件**……经由**网址（URL）**来识别与访问……通过**浏览器**解释网页的内容……  

所以网页相当于一个压缩包，网址就是下载链接，浏览器就是解压缩软件，而我们看到的是压缩包内的文档——这么说是不是很好理解。

而爬虫的思想：“处理网址——抓取页面——寻找页面信息——再次处理网址/打印爬取结果”翻译成白话就是“找到下载链接——下载&解压缩——查找我们需要的文档——再次找到链接/收工”。听上去还挺简单的，那么我们来分别实现一下。

## 分步实验
### 处理网址
字符串的处理，就是这么简单。
`url = 'https://github.com'`

### 抓取页面
这里我们要用到 Requests 模块。

> Requests 唯一的一个非转基因的 Python HTTP 库，人类可以安全享用。  
> 警告：非专业使用其他 HTTP 库会导致危险的副作用，包括：安全缺陷症、冗余代码症、重新发明轮子症、啃文档症、抑郁、头疼、甚至死亡。[Requests: 让 HTTP 服务人类 — Requests 2.18.1 文档](http://cn.python-requests.org/zh_CN/latest/)  

既然人家官网都这么写了，想必这个模块是方便的——至少足够安全。那么在一切开始之前，我们需要安装：
`$ pip install requests`

现在我们就可以运行第一个使用 Requests 的程序了：
```python
>>> import requests
>>> url = 'https://github.com'
>>> r = requests.get(url)
```
就这么简单，你会获得一个 response 对象。

```python
# 网页标头
print r.headers
# 以字节的方式访问请求响应体
print r.content
# 原始响应内容
print r.raw
# 返回 Requests 使用的编码
print r.encoding
```

当然运行结果可不简单，那一片乱七八糟的东西，先不去管它。




```python
# -*- coding:utf-8 -*-

"""
一个简单的python爬虫框架
Authou: zolars
Version: 1.0
Date: 2017-08-30
Language: Python2.7.10
Modules:
    - requests
    - chardet
    - re
Editor: Atom 1.19.4
"""

import requests
import chardet
import re


class Spider(object):
    """类说明
    用于抓取网站信息的爬虫
    """
    user_agent = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.113 Safari/537.36'
    self.headers = {'User-Agent': user_agent}

    # 初始化数据库
    self.data = []

    print '类声明完毕...'

    print '爬虫准备就绪,开始爬取数据...'

    def __init__(self):
        """函数说明
        类声明
        """
        print '类声明完毕...'
        pass

    def spider_start(self):
        """函数说明
        爬虫入口, 控制页面信息
        """
        print '爬虫入口完毕...'
        pass

    def get_page(self, cur_page):
        """函数说明
        根据当前页码抓取网页HTML信息
        """
        print '抓取{cur_page}页面信息完毕...'
        pass

    def match(self, page):
        """函数说明
        使用正则表达式匹配传入的网页HTML
        """
        print '正则表达式匹配完毕...'
        pass

    def print_result(self):
        """函数说明
        打印爬取结果
        """
        print '打印爬取结果完毕...'
        pass


def main():
    my_spider = Spider()
    my_spider.spider_start()
    print '爬虫全部运行完毕...'


if __name__ == "__main__":
    main()

```
