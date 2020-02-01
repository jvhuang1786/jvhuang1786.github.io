---
layout: archive
permalink: /disney_nlp/
title: "Disney Parks Twitter NLP"
author_profile: true
header:
  image: "/images/sf.jpg"
---

# NLP Disney Parks brief introduction

## Cleaning and Wrangling

* Libraries
- Tweepy
- re
- emoji
- numpy
- bs4
- pandas
- document
- string

* Twitter sentiment analysis was done for both the Disney Parks.  To collect data I used the Twitter API and collected livestream tweets.  Collection was done for the Halloween seasonal 2019 and Chinese New Year 2020 events at both Tokyo Disney Resort and Anaheim Disney Resort.  

* To clean and structure the data the tweepy library was used. Regular expression was used to clean the data and retrieve hashtags,links, mentions and emojis

1. Nested dictionaries were pulled out to consolidate the text.
2. Date time was formatted
3. Numerical data that was used replaced NaNs with 0's
4. Hashtags, Emoticons, Mentions, Links were all put in their own column    

* To do a comparable analysis of Japanese text and English text, word and google translation service was used.  After a text sentiment analyzer was applied to the text data.

The following libraries/modules were used for sentiment labeling.

* NLTK Vader
* Text Blob
* Asari - was overly positive.  Was developed by a python developer on [qiita](https://qiita.com).
* R Sentiment from the cran package.

* Comparison was made between NLTK, Text Blob and R Sentiment.  If two analyzers voted positive then positive was chosen for the text sentiment label.  For any remaining ones that a decision couldn't be reached NLTK Vader was used.  

* Geocoder was used to add back in longitude and latitude data for user location.  

## Exploratory Data Analysis

* Libraries
- seaborn
- matplotlib
- bokeh
- plotly
- Spacy ScatterText
- Folium
- Basemap
- wordcloud




[Disney NLP Write UP](https://docs.google.com/document/d/1pCiP9xJWBGO8QNteLKqXBVSPj5HfoKziGyEEvUe_xvY/edit)


[Disney NLP Github](https://github.com/jvhuang1786/DisTweetCapstone)

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag| slugify }}" class ="archive_subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
