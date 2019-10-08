---
title: Python ❤ Echarts - Making an airline Echarts
date: 2018-11-19 14:49:37
categories: Study
tags:
- python
- Web Design
thumbnail:
---

> By IDP project, I learned about Echarts on javascript. With this experiences, I took a job yesterday: Making a demo webpage for airlines. Originally, I purpose to write this with JS code and HTML but I just wanna make this page expansionable and 'agile'. Complementing this with Python Flask structure and explore pyecharts package seems good. Anyway, these days are too boring without any job​. Time to work 🙌

<!--more-->

## Requirements

1. In the main page, draw global 2D map. On the left of page, add window with a user list.
2. Click on a user on the right to draw all the aircraft routes (dynamic effects) related to the user on the global 2D map, and display the user details window on the left side of the page; when the user is clicked again, the relevant route of the user is hidden, user details are hidden as well in information window.

## Implements

1. With Flask

    Flask is a lightweight [WSGI](https://wsgi.readthedocs.io/) web application framework. With specific website templates and Jinja2, I can easily build a direct and fast web app. It is also a good method for visualization with Python script.

2. With Echarts

    Echarts, a brilliant JavaScript charts lib. I'm deeply impressed by it. As an open-sourced, web-based, cross-platform framework, implements uncredible stablity and performance with Streaming architecture. Consequently, Echarts make the best practice for the extensibility of JS code. 
   
    However, just the original JS code is too redundancy. We don’t want to update charts every time when the page is generated. So with the help of Python script, we can load the airlines data into the original html without any JS logic.

3. With Pyecharts

    In summary, I decided to code with Pyecharts and Flask. Just operate one language, Python, for the whole task, which is really convenience. Firstly, fill the json data in python. Secondly, generate the Echarts JS code through python script. In the end, deploy the JavaScript with Flask templates and show the pages in browsers. What's more, I still had approach to save the full html and JS so that we can move them everywhere.

## Achievements

[Click to see the website!](./cas-airline.html)

Highlights for the simple file tree: 

```
.
├── app.py
├── airports.json
├── data.json
└── templates
    ├── image
    │   ├── user.png
    ├── macro
    └── simple_chart.html
    ```

`airports.json` and `data.json` are the data json. 

With the source code, `app.py` which is no more than 150 lines, we can realize the whole website. Obviously, this work approach conspicuously reduced workloads and make your life easier as a programmer😀


