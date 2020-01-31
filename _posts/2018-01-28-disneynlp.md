---
title: "Disney NLP: Analysis of Tokyo and Anaheim Disney Resorts"
date: 2020-01-30
tags: [data wrangling, data science, nlp]
header:
excerpt: "Natural Language Processing, Disney, Data Science"
mathjax: "true"
---

### Intro

The project was inspired by my summer trip to Tokyo Disneyland.  Researching guides on youtube there was a huge number of Youtubers, people on reddit, twitter and other forms of media claiming Tokyo Disney Resort specifically Tokyo Disney Sea was the best Disney park.  The park that would make Walt Disney proud.

The business use of doing NLP for both Disney resorts would be help Imagineers come up with new decorative themes for the park during seasonal events.  By seeing trends of what people liked and disliked it can help relay information to Disney's business partners of what worked and didn't work.

So what is an Imagineer you might ask?

Imagineers are in charge of dreaming, designing and building Disney theme parks, attractions, cruise ships, resorts etc. Basically, they’re about live entertainment. They create things you can see and touch and smell, experiences that you can walk right into. They're the ones who create the experience and allow visitors to emerge themselves into the world of Disney.  For example, the new Galaxy Edge now allows Star Wars fans for a place to gather and enjoy themselves on Batuu.  

###Twitter API

Data was collected through the Twitter API from September 24th, 2019 to November 1st, 2019.  Both parks were running their halloween themed festival.  

Tokyo Disney - Spooky Boo Halloween Parade

Anaheim Disney - Oogie Boogie Bash

The following was searched for using Tweepy and the Twitter API

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/hashtags.png" alt="wordcloud, disney, nlp" width="200" height="100">

This was result I ended up with.

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/unclean.png" alt="wordcloud, disney, nlp" width="200" height="100">



### Data Wrangling/Cleaning

Tweepy does the strange thing of separating text that you collect into four separate nested dictionaries.

* extended_tweet
* extended_entities
* retweeted_status
* text
* quoted_status


 Following code was used to pull out the full text from a nested dictionary.  There were times I had to pull a nested dictionary from a nested dictionary as well.

```python
#pull out extended Tweets
df['ex_tw_full_text'] = [d.get('full_text') if type(d) == dict else np.nan
                          for d in df['extended_tweet']]
```

#### Exploratory Data Analysis

<p> Below shows a wordcloud visualization of English twitter user data.  The most common words are fuck and annual pass.  One of the most common retweets happening during the collection period was a tweet about someone trying to get in with a fake annual pass.<p>

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/cinderella.jpg" alt="wordcloud, disney, nlp" width="200" height="100">





<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/scatter.gif" alt="scattertext, disney, nlp" width="2200" height="3000">




#### Statistics

Here's some inline code `x+y`.

Here's some math:

$$z=x+y$$

You can also put it inline $$z=x+y$$


<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/correlation.jpg" alt="correlation, disney, nlp" width="400" height="400">


#### Machine Learning




##### Supervised Learning



##### Unsupervised Learning




#### Model in Action for Chinese New Year Event Tweets

Below is the link to a model you can use for yourself.

[Disney NLP Model Start to Finish](https://github.com/jvhuang1786/DisTweetCapstone/blob/master/dis_model_production.ipynb)
