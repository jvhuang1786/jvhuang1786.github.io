---
title: "Disney NLP: Analysis of Tokyo and Anaheim Disney Resorts"
date: 2020-01-30
tags: [data wrangling, data science, nlp]
header:
excerpt: "Natural Language Processing, Disney, Data Science"
mathjax: "true"
---

# Intro

The project was inspired by my summer trip to Tokyo Disneyland.  Researching guides on youtube there was a huge number of Youtubers, people on reddit, twitter and other forms of media claiming Tokyo Disney Resort specifically Tokyo Disney Sea was the best Disney park.  The park that would make Walt Disney proud.

The business use of doing NLP for both Disney resorts would be help Imagineers come up with new decorative themes for the park during seasonal events.  By seeing trends of what people liked and disliked it can help relay information to Disney's business partners of what worked and didn't work.

So what is an Imagineer you might ask?

Imagineers are in charge of dreaming, designing and building Disney theme parks, attractions, cruise ships, resorts etc. Basically, they’re about live entertainment. They create things you can see and touch and smell, experiences that you can walk right into. They're the ones who create the experience and allow visitors to emerge themselves into the world of Disney.  For example, the new Galaxy Edge now allows Star Wars fans for a place to gather and enjoy themselves on Batuu.  

# Twitter API Data Collection

Data was collected through the Twitter API from September 24th, 2019 to November 1st, 2019.  Both parks were running their halloween themed festival.  

Tokyo Disney - Spooky Boo Halloween Parade

Anaheim Disney - Oogie Boogie Bash

The following was searched for using Tweepy and the Twitter API

Disney Anaheim      | Disney Tokyo
--------------------|---------------
disneylandresort    | disneysea
disneyland          | disneytokyo
disneyresort        | disneytokyoresort
californiaadventure | tokyodisneyresort
downtowndisney      | tokyodisneyland
disneyanaheim       | 東京ディズニーランド
dca                 | ディズニーランド
disneylandanaheim   | 東京ディズニーシー
disneycalifornia    | ズニーシー
californiadisney    | tdr_now
                    | tdr_md



After collection everything ended up in a json file.

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/unclean.png" alt="wordcloud, disney, nlp" width="1000" height="1000">



# Data Wrangling/Cleaning

Tweepy does the strange thing of separating text that you collect into four separate nested dictionaries.

* extended_tweet
* extended_entities
* retweeted_status
* text
* quoted_status


 Following code was used to pull out the full text from a nested dictionary.  There were times I had to pull a nested dictionary from a nested dictionary as well.

```python
df['ex_tw_full_text'] = [d.get('full_text') if type(d) == dict else np.nan
                          for d in df['extended_tweet']]
```



# Exploratory Data Analysis

Below shows a WordCloud visualization of English twitter user data.  The most common words are fuck and annual pass.  One of the most common retweets happening during the collection period was a tweet about someone trying to get in with a fake annual pass.

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/cinderella.jpg" alt="wordcloud, disney, nlp" width="300" height="200">

Things like the experience, lottery tickets for the show One Mans Dream was being talked about the most in the Japanese text WordCloud visualization.

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/japanese.png" alt="wordcloud, disney, nlp" width="700" height="700">


ScatterText part of the Spacy library was used.  ScatterText allows you to look up certain words and shows you in which document in the corpus the word shows up in.  I compared translated Japanese text to English text.


<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/scatter.gif" alt="scattertext, disney, nlp" width="2200" height="3000">




# Statistics

The hypothesis:

H<sub>0</sub> = English and Japanese Twitter users have the same Text Blob polarity or Vader Compound with their sentiment to the Disney Parks during the Halloween event.

H<sub>0</sub> : μ<sub>1</sub> ≠ μ<sub>2</sub>


H<sub>A</sub> = English and Japanese twitter users have different Text Blob polarity or Vader Compound with their sentiment towards the Disney Parks during the Halloween event.

H<sub>A</sub> : μ<sub>1</sub> ≠ μ<sub>2</sub>


alpha = 0.05


Params:           |Vader Compound Score | Text Blob Polarity
------------------|---------------------|-----------------------
Mean difference   | -0.1117             | -0.0101
------------------|---------------------|-----------------------
t-stat            |47.4353              | 7.9732
------------------|---------------------|-----------------------
p-value           | 0.000               | 0.000




Params:           |Vader Score Mean     | Text Blob Score Mean
------------------|---------------------|-----------------------
English           | 0.114               | 0.543
------------------|---------------------|-----------------------
Japanese          | 0.226               | 0.482




Mann-Whitney U Test non-parametric distribution test

Tests whether the distributions of two independent samples are equal or not.

H<sub>0</sub> : the distributions of both samples are equal.

H<sub>A</sub> : the distributions of both samples are not equal.

Japanese Twitter users vs English Twitter Users

Params |Vader Compound Score | Text Blob Polarity
-------|---------------------|-----------------------
stat   | 4493129062.500      | 4867484730.500
-------|---------------------|-----------------------
p-value| 0.000               | 0.000




Correlation Matrix

<img src="{{ site.url }}{{ site.baseurl }}/images/disneynlp/correlation.jpg" alt="correlation, disney, nlp" width="1000" height="1000">


# Machine Learning

## Preprocessing the text

```python
stopwords = nltk.corpus.stopwords.words('english')
wn = nltk.WordNetLemmatizer()
punc = lambda x: re.sub("!|,|\?|\'|-|\"|&|。|\)|\(|！|，|\.*|/|\[|\]|\u2026|\d|:|~|、|？|☆|’|– |【|】|「|」|《|》|※| “|”|＊|→||[\b\.\b]{3}||@||@ |#|# |", '',x)

#Clean
def clean_text(soup):
    soup = BeautifulSoup(soup, 'lxml')
    souped = soup.get_text()
    stripped = re.sub(r'https?://[A-Za-z0-9./]+', '', souped)
    words = stripped.split()
    mention = [word for word in words if not word.startswith('@')]
    RT = [word for word in mention if not word.startswith('RT')]
    text = " ".join([wn.lemmatize(word) for word in RT if word not in stopwords])
    punct = "".join([word.lower() for word in text if word not in string.punctuation])
    short_words = ' '.join([w for w in punct.split() if len(w)>2])
    ja_punct = ''.join([punc(word) for word in short_words])
    tokens = re.split('\W+', ja_punct)
    return (" ".join(tokens)).strip()
```

## Supervised Learning

Random Forest Classifier Countvectorizer

```python
rf_clf = RandomForestClassifier()

hyperparameters = {
    'n_estimators': range(50,1000,100),
    'max_depth': [5,50,100, 200, 300, 400, 500],
    'max_features': ['auto', 'sqrt', 'log2']
}

clf = RandomizedSearchCV(rf_clf, hyperparameters, cv=5, n_jobs=-1,
                         n_iter = 10, random_state = 77)
%time rf_cv_fit = clf.fit(X_count_r, y_r)
```

## Unsupervised Learning

LDA Topic Modeling

```python
lda_model = gensim.models.ldamodel.LdaModel(corpus=corpus,
                                           id2word=id2word,
                                           num_topics=4,
                                           random_state=777,
                                           update_every=1,
                                           chunksize=10,
                                           passes=10,
                                           alpha='symmetric',
                                           iterations=100,
                                            per_word_topics=True)
```

# Model in Action for Chinese New Year Event Tweets

Below is the link to a model you can use for yourself.

[Disney NLP Model Start to Finish](https://nbviewer.jupyter.org/github/jvhuang1786/DisTweetCapstone/blob/master/dis_model_production.ipynb)
