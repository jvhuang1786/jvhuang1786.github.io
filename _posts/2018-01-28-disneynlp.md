---
title: "Disney NLP: Analysis of Tokyo and Anaheim Disney Resorts"
date: 2020-01-30
tags: [data wrangling, data science, nlp]
header:
excerpt: "Natural Language Processing, Disney, Data Science"
mathjax: "true"
---


##### The project was inspired by my summer trip to Tokyo Disneyland.  Researching guides on youtube there was a huge number of Youtubers, people on reddit, twitter and other forms of media claiming Tokyo Disney Resort specifically Tokyo Disney Sea was the best Disney park.  The park that would make Walt Disney proud.  We will run various ML modes to try to predict user sentiment.  Using Microsoft word translation to translate the text from Japanese twitter users to be able to compare them with English twitter users.

#### Some of the questions I hope to answer are:

* Do Japanese twitter users have a more positive sentiment towards the Disney Parks vs English users?
* Is there something at Tokyo Disney resort that users are tweeting more about than Anaheim Disney resort?  
* Does Oriental Land or other local Japanese businesses do a better job promoting the Disneyland during a Seasonal event on twitter vs their English counterpart?   
* What cultural differences can we find on twitter between Japanese and English users?


#### Data Wrangling/Cleaning

Python code block:
```python
    import numpy as np

    def test_function(x, y):
      z = np.sum(x,y)
      return z
```

#### Exploratory Data Analysis

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/cinderella.jpg" alt="wordcloud, disney, nlp" width="200" height="100">



<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/scatter.gif" alt="scattertext, disney, nlp" width="2200" height="3000">

#### Statistics

Here's some inline code `x+y`.

Here's some math:

$$z=x+y$$

You can also put it inline $$z=x+y$$

#### Machine Learning

##### Supervised Learning

##### Unsupervised Learning

#### Conclusion

Below is the link to a model you can use for yourself.

[Disney NLP Model Start to Finish](https://github.com/jvhuang1786/DisTweetCapstone/blob/master/dis_model_production.ipynb)
