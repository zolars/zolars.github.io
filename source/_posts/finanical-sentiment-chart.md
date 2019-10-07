---
title: Finanical Sentiment Chart <br> Easy to analysis Finance with Tweets' Sentiments
date: 2019-07-01 23:41:07
categories: Study
tags:
- Scrapy
- python
- Web Design
thumbnail: https://raw.githubusercontent.com/zolars/typora-user-images/master//img/20191007211343.png

---

## Abstract

Finanical Sentiment Chart aims to analyse influence between social sentiment and financial tendency. This is a cooperation project with [Oscar Osborne](https://www.linkedin.com/in/oscarosborne), Ph.D of the University of New South Wales.

This project uses scraper with high performance to get large scale data of tweets. With these data, run sentiment analysis in order to generate a realtime update chart. The raw data is also saved in database, which may provide further analysis.

<!--more-->

<iframe allowtransparency="false" height="350" src="https://drive.google.com/file/d/12Z8ZbeNHNtZHSf6XzPC5iZj8-QX8_Zso/preview" width="100%"></iframe>
<p align="center"><i>👆Please watch the video to get a highlight</i></p>

## Objective

To develop a platform which gathers live financial data and social network/online information/media information which will be displayed in a HTML format. The dataset will be used to analyze the relationship between online social sentiment of a certain stock, share, currency, crypto, and that stock price over a period of time.

Basically, this data aims to find is how social sentiment impacts price of:

* Stock exchanges
  * Shares within those exchanges
* Global currencies
* Crypto currencies

In order to find the social sentiment of a stock, the program will use keywords to identify that the social media post is actually talking about that stock. I think that the best way to classify whether the post is speaking about a financial stock would be through the stock abbreviation code, the name of the stock or the name of the CEO, etc.

What's more, this Web application is built as a financial analysis tool. Consequently, I hope that **anyone whether owned programming experiences or not**, can easily run and deploy this service.

## Implementation

I made a realtime scraper with high performance in order to catch data from [Twitter](https://www.twitter.com) and [Weibo](https://www.weibo.com). The data is saved in MySQL database and execute sentiment analysis with a pipeline.

![MySQL Database](https://raw.githubusercontent.com/zolars/typora-user-images/master/20190707234203.png)

After that, I build a light-wight Web application with Python Flask and ECharts. The application can be easily deployed on any server with python environment and it can run realtime, stably and automatically. I will give you the deploy method.

Find more about this project on my [GitHub](https://github.com/zolars/financial-sentiment) 🙋‍

## Usage

1. Get the code from Github clone or download zip by clicking [this](https://github.com/zolars/financial-sentiment/archive/master.zip).
    ```
    $ git clone https://github.com/zolars/finanical-sentiment.git
    ```

2. You need to install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) and [MySQL](http://dev.mysql.com/downloads/mysql/) on your computer.
    ```
    $ conda -V
    conda 4.7.10
    ```

    You need to set "123456" as the MySQL password. Or change the password in the code.

    ```
    $ mysql -u root -p
    Enter password:123456
    Welcome to the MySQL monitor.  Commands end with ; or \g.
    ```

3. Create the environment.
    ```
    $ cd finanical-sentiment
    $ conda env create -f environment.yml
    $ conda activate finance
    $ python -V
    Python 3.6.8 :: Anaconda, Inc. 
    ```

    If you want to update your environment, use:
    ```
    $ conda env update -f environment.yml
    ```

4. Download dependencies.
    ```
    $ python -m textblob.download_corpora
    ```

5. Create a new DATABASE with MySQL.
    ```
    $ mysql -u root -p
    Enter password:123456
    mysql> create DATABASE posts;
    mysql> use posts;
    Database changed
    ```

6. Run the app
    ```
    $ cd finanical-sentiment
    $ conda activate finance
    $ python app.py
    ```

## Twitter Advanced Search Options

### How to use 'Advanced Search' to generate query?

1. With this website, input any keywords you want to search for.
    ![](https://raw.githubusercontent.com/zolars/typora-user-images/master/20190724022657.png)
2. Click 'Search for' button.
3. In the new page, copy the query you need as below:
    ![](https://raw.githubusercontent.com/zolars/typora-user-images/master/20190724023017.png)

### Code Options

| Operator                               | Finds tweets...                                                           |
| -------------------------------------- | ------------------------------------------------------------------------- |
| twitter search                         | containing both "twitter" and "search". This is the default operator.     |
| **"**happy hour**"**                   | containing the exact phrase "happy hour".                                 |
| love **OR** hate                       | containing either "love" or "hate" (or both).                             |
| beer **-** root                        | containing "beer" but not "root".                                         |
| **#** haiku                            | containing the hashtag "haiku".                                           |
| **from:** alexiskold                   | sent from person "alexiskold".                                            |
| **to:** techcrunch                     | sent to person "techcrunch".                                              |
| **@** mashable                         | referencing person "mashable".                                            |
| "happy hour" **near:** "san francisco" | containing the exact phrase "happy hour" and sent near "san francisco".   |
| **near:** NYC **within:** 15mi         | sent within 15 miles of "NYC".                                            |
| superhero **since:** 2010-12-27        | containing "superhero" and sent since date "2010-12-27" (year-month-day). |
| ftw **until:** 2010-12-27              | containing "ftw" and sent up to date "2010-12-27".                        |
| movie -scary **:)**                    | containing "movie", but not "scary", and with a positive attitude.        |
| flight **:(**                          | containing "flight" and with a negative attitude.                         |
| traffic **?**                          | containing "traffic" and asking a question.                               |
| hilarious **filter:links**             | containing "hilarious" and linking to URLs.                               |
| news **source:twitterfeed**            | containing "news" and entered via TwitterFeed                             |

### Where is the export Excel files?

They locate at `./out/`.