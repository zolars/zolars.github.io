---
title: Constructure of Waterbirds recognition interface service
date: 2019-04-29 10:14:08
categories: Study
tag: 
  - CS
toc: true
---

Good News! After getting the domian name, we finished pressure testing. The average processing efficiency is up to 12 requests per second and theoretically, the service can support 400 users simultaneously. 

Now you can try the service by visiting this page and upload a waterbird's picture such as Red-breasted merganser: https://birdid.iscas.ac.cn:8080/upload/

![](https://raw.githubusercontent.com/zolars/pic-bed/master/20191011003200.png)
<p align="center">Red-breasted merganser</p>

<!--more-->

---

Recently, I got the remote access key of our servers located at laboratory, which was a brilliant good news meaning that I can have fun with the 4-WAY SLi PASCAL TITAN Xp anywhere and anytime! Of course not running games, don't think that. I had a job, trying to convince myself :)

After the BCNN model's constructure in the last three months, my new target is to deploy the recongition service online 24/7. In course of the institute's powerful servers, which is actually the most powerful servers I've seen before, I didn't care about the recognition fps at first. But in practise, the real performance is low, seems like it was running the model on my laptop without GPUs...It took almost two minutes to give one result!

It shocked me for a while though I clearly know why it had happened. The report I handed in months before mentioned that problem.

> Noticing that deploying the model costs too many time, the next goal is to realize the feasible and high-quality method to reduce time cost on rebuilding the model. When using the model to identify birds, can the model instance be kept in memory once completely loaded?

The problem occured when I run my training on the PC with just one Titan Xp. I assumed four Titan Xp will be better? The reality is worse. To keep the model instance in memory once completely loaded needed to be done. At the same time, we had to regard that the large amount of requests and image cache may increase the servers' stress. I decided to deploy this model with Flask and nginx+Gunicorn on Ubuntu. The code isn't sophisticated:

```python
@app.route('/upload/', methods=['GET', 'POST'])
def main_page():
    if request.method == 'POST':
        file = request.files['file']
        if file and allowed_file(file.filename):
            # filename = secure_filename(file.filename)
            # file.save(os.path.join(app.config['UPLOAD_FOLDER'], filename))
            results = model.test(Image.open(file))
            ...
            ...
```

With multiple threads, we loaded about ten instances of the model in memory. When the requests came in, Flask responses them by calling functions with decorator ` @app.route(...)`. Furthermore, the function's return is the response of this request. Enough intuitive. Easier than Java Servlets' separate logic (certainly slower). 

The Gunicorn was used to manage and deal with high concurrency. `-w` parameter is the amount of workers. With `nohup` to keep the service online all the time. 

```bash
gunicorn -w 4 -b 127.0.0.1:8000 service:app
```

In the end, set the nginx point to http://127.0.0.1:8000. All done. The flow is a little long, as the README is. 

![](https://raw.githubusercontent.com/zolars/pic-bed/master/20191010232000.png)

The last step is linked the service to Internet domain name which wasn't provided by my professor yet, so I just run this "minimalism" page with localhost. We haven't been able to test the concurrency even though that is the key puzzle. I will keep it in sight 

Currently, the commercialisation of cloud deep learning servers has set up, and the large scale cloud computing vendors are competeing to take over all of the market. Companies include Deep Learning on AWS by Amazon, Machine Learning Studio by Microsoft, Cloud Platform by Google, PaddlePaddle Online by Baidu, TI-ML by Tencent, and ML Pai by Alibaba. In addition, more and more deployment technologies are created. iOS and Android both developed AI Core in order to run ML services on mobile phones. Maybe AI's mobile deployment on IOT is the next trending on CS.