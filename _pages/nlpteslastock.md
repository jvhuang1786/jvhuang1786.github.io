---
layout: archive
permalink: /timeseries_stockpred/
title: "Time Series with NLP Stock Prediction"
author_profile: true
header:
  image: "/images/berttimeseries/logo.png"
---

## Can we use Elon's Tweets to make a better Multivariate Time Series Model?

### Libraries

  * scipy
  * statsmodel
  * plotly
  * pandas_datareader
  * seaborn
  * streamlit
  * wordcloud
  * PIL
  * bs4
  * bokeh
  * gensim
  * huggingface
  * ktrain
  * pytorch
  * tensorflow

### How Data was collected

  * Data was collected using pandas_datareader for financial data and GetOldTweets3 for twitter data
  * User handle was elonmusk and data collection period was Dec 1, 2011 to July 31, 2020
  * Running a non-parametric test between no-tweets, personal-tweets and business tweets showed a price difference in closing price between the 3

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/1.png" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/2.png" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/3.png" alt="timeseries, tesla, nlp" width="800" height="800">

### Text Classification

  * More traditional Classification models were first experimented with before moving to transformer architecture.  
  * They had very low f1-score the best being logistic regression at 0.62

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/4.png" alt="timeseries, tesla, nlp" width="800" height="800">

  * Using BERT and DistilBERT f1-score was around 0.80
  * Used DistilBERT because the model was much smaller and would be much easier to launch as a webapp

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/5.png" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/6.png" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/7.png" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/8.png" alt="timeseries, tesla, nlp" width="800" height="800">

### Time Series Models

  * I tried again to use sklearn models before turning to neural networks.
  * I tried a xgboost and randomforest however because of the structure and how volatile Tesla stock price was these algorithms probably wouldn't be suitable
  * I also tried using ARIMA but usually that is only for univariate time series models.

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/9.gif" alt="timeseries, tesla, nlp" width="800" height="800">

### RNN, LSTM, GRU

  * GRU gave the best results.  
  * I changed some of the structure in GRU below which gave a slightly better prediction.
  * Changing the recurrent activation and activation  

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/10.gif" alt="timeseries, tesla, nlp" width="800" height="800">

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/11.png" alt="timeseries, tesla, nlp" width="800" height="800">

### Out of sample data

  * Doing a 0.90 Train, 0.1 Test I felt did not give me much data to work with
  * I further used August 1, 2020 to August 13th, 2020 as a validation set
  * Below are the results and it made a huge miss on August 12th, 2020 the announcement of the stock split.

<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/12.gif" alt="timeseries, tesla, nlp" width="800" height="800">

### What to improve on

  * Use 8-k data from SEC. Scrape it and analyze the text
  * Use prominent business tweeters instead of Elon as they talk more about the business of Tesla
  * Instead of classifying as type and sentiment separate them in bins of gains and losses based on the text.
<img src="{{ site.url }}{{ site.baseurl }}/images/berttimeseries/13.png" alt="timeseries, tesla, nlp" width="800" height="800">

* More information and details on the write up can be found in the webapp. Github link also below:

[Tesla Web App](https://elon-tesla.herokuapp.com)

[Tesla Github Repo](https://github.com/jvhuang1786/teslaElonStockpred)
