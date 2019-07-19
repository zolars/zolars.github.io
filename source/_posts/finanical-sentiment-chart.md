---
title: Finanical Sentiment Chart <br> Easy to analysis Finance with Tweets' Sentiments
date: 2019-07-01 23:41:07
categories: Coding
tags:
- Scrapy
- python
---

<iframe allowtransparency="false" height="350" src="https://drive.google.com/file/d/12Z8ZbeNHNtZHSf6XzPC5iZj8-QX8_Zso/preview" width="100%"></iframe>

<!-- <img src="https://raw.githubusercontent.com/zolars/typora-user-images/master/20190715132829.png" class="full-image" /> -->

## Abstract

Finanical Sentiment Chart aims to analyse influence between social sentiment and financial tendency. This is a cooperation project with Oscar Osborne, Ph.D of the University of New South Wales. 

This project uses scraper with high performance to get large scale data of tweets. With these data, run sentiment analysis in order to generate a realtime update chart. The raw data is also saved in database, which may provide further analysis.

<!--more-->

## Objective

To develop a platform which gathers live financial data and social network/online information/media information which will be displayed in a HTML format. The dataset will be used to analyze the relationship between online social sentiment of a certain stock, share, currency, crypto, and that stock price over a period of time.

Basically, this data aims to find is how social sentiment impacts price of:

* Stock exchanges
  * Shares within those exchanges 
* Global currencies
* Crypto currencies

In order to find the social sentiment of a stock, the program will use keywords to identify that the social media post is actually talking about that stock. I think that the best way to classify whether the post is speaking about a financial stock would be through the stock abbreviation code, the name of the stock, the name of the CEO.

What's more, this Web application is built as a financial analysis tool. Consequently, I hope that anyone, with or without programming experiments, can easily run and deploy this service.

## Implementation

I made a realtime scraper with high performance in order to catch data from [Twitter](https://www.twitter.com) and [Weibo](https://www.weibo.com). The data is saved in MySQL database and execute sentiment analysis with a pipeline.

![MySQL Database](https://raw.githubusercontent.com/zolars/typora-user-images/master/20190707234203.png)

After that, I build a light-wight Web application with python flask and echarts. The application can be easily deployed on any server with python environment and it can run realtime, stably and automatically. I will give you the deploy method and a video as instructions.

## Usage

1. You need to install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) and [MySQL](http://dev.mysql.com/downloads/mysql/) on your computer.
    ```bash
    $ conda -V
    conda 4.6.xx
    ```

2. Get the code from Github clone.
    ```bash
    $ git clone https://github.com/zolars/finanical-sentiment.git
    ```

3. Create the environment.
    ```bash
    $ cd finanical-sentiment
    $ conda create -n finance python=3.6
    $ conda activate finance
    $ python -V
    Python 3.6.8 :: Anaconda, Inc. 
    ```

4. Install dependencies.
    ```bash
    $ conda activate finance
    $ conda install -c conda-forge scrapy
    $ python -m pip install -r requirements.txt
    $ python -m textblob.download_corpora
    ```

5. Create a new DATABASE with MySQL.
    ```
    $ mysql -u root -p
    Enter password:******
    mysql> create DATABASE finance;
    mysql> use finance;
    Database changed
    ```

6. Modify the configuration.

    Modify the keywords `QUERY` and `MYSQL_TABLE_NAME` in `TweetScraper/settings.py`. 
    
    1. The `MYSQL_TABLE_NAME` keyword is as same as the stock code. For example:

        ```
        MYSQL_TABLE_NAME = "GOOG"
        ```

    2. The `QUERY` is the keyword for [Twitter Search](https://twitter.com/search-home).
        Tips: use Twitter operators for advanced search.

7. Run the app
    ```bash
    $ cd finanical-sentiment
    $ conda activate finance
    $ python tweet_engine.py
    ```

    ```bash
    $ cd finanical-sentiment
    $ conda activate finance
    $ python charts_engine.py
    ```

## Instruction video

<iframe allowtransparency="false" height="350" src="https://drive.google.com/file/d/1mN2Z0HMtFhZDKGTV_bnvgkWmrQjhAOH5/preview" width="100%"></iframe>

## Twitter Search Opeartors

|                Operator                |                              Finds tweets...                              |
| :------------------------------------: | :-----------------------------------------------------------------------: |
|             twitter search             |   containing both "twitter" and "search". This is the default operator.   |
|          **"**happy hour**"**          |                 containing the exact phrase "happy hour".                 |
|            love **OR** hate            |               containing either "love" or "hate" (or both).               |
|            beer **-** root             |                     containing "beer" but not "root".                     |
|              **#** haiku               |                      containing the hashtag "haiku".                      |
|          **from:** alexiskold          |                      sent from person "alexiskold".                       |
|           **to:** techcrunch           |                       sent to person "techcrunch".                        |
|             **@** mashable             |                      referencing person "mashable".                       |
| "happy hour" **near:** "san francisco" |  containing the exact phrase "happy hour" and sent near "san francisco".  |
|     **near:** NYC **within:** 15mi     |                      sent within 15 miles of "NYC".                       |
|    superhero **since:** 2010-12-27     | containing "superhero" and sent since date "2010-12-27" (year-month-day). |
|       ftw **until:** 2010-12-27        |            containing "ftw" and sent up to date "2010-12-27".             |
|          movie -scary **:)**           |    containing "movie", but not "scary", and with a positive attitude.     |
|             flight **:(**              |             containing "flight" and with a negative attitude.             |
|             traffic **?**              |                containing "traffic" and asking a question.                |
|       hilarious **filter:links**       |                containing "hilarious" and linking to URLs.                |
|      news **source:twitterfeed**       |               containing "news" and entered via TwitterFeed               |
