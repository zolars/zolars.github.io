---
title: Python ❤ Echarts - Making an airline echarts
date: 2018-11-19 14:49:37
categories: Study
tags:
- python
- Web Design
thumbnail:
---

> By IDP project, I learned about Echarts on javascript. With this experiments, my fellows give me a task yesterday： Making a demo webpage for airlines. Originally, I purpose to write this with JS code and HTML but I just wanna make this page expansionable and 'agile'. Let me finish this with Python Flask structure and explore pyecharts 
> package. Anyway, these days are too boring without any job​🙌.

<!--more-->

## Requirements

1. In the main page, draw global 2D map. On the left of page, add window with a user list.
2. Click on a user on the right to draw all the aircraft routes (dynamic effects) related to the user on the global 2D map, and display the user details window on the left side of the page; when the user is clicked again, the relevant route of the user is hidden, user details are hidden as well in information window.

## Implements

1. With Python Flask

   Flask is a lightweight [WSGI](https://wsgi.readthedocs.io/) web application framework. With specific website templates and Jinja2, I can easily build a direct and fast web app. It is also a good method for visualization with Python script.

2. With echarts

   Echarts, a brilliant JavaScript charts lib. However, just the original JS code is too redundancy. We don’t want to update charts every time when the page is generated. So with the help of Python script, we can load the airlines data into the original html without any JS logic.

3. With Pyecharts
4. 