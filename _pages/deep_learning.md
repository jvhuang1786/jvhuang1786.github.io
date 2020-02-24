---
layout: archive
permalink: /deep_learning/
title: "Deep Learning"
author_profile: true
header:
  image: "/images/culture.png"
---

# Generative Adversarial Networks

## Intro

  * The goal is to use neural networks to try to generate concept art.  

  * Below is testing on NVIDIA style GAN 2.0.  

  * Deep convolutional GAN was also experimented on.  Will publish more as I progress further.

  * Goal is to try to produce full body images. Looking at LOL data and monster hunter hunter data.

**Style GAN 2.0**

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/face.gif" alt="text, previz, deeplearning" width="1500" height="1500">
</p>

**DCGAN 10000 Steps**

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/dcganface.gif" alt="text, previz, deeplearning" width="1500" height="1500">
</p>

**DCGAN 100000 Steps**

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/100000.png" alt="text, previz, deeplearning" width="1500" height="1500">
</p>

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag| slugify }}" class ="archive_subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
