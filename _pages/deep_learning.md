---
layout: archive
permalink: /deep_learning/
title: "Deep Learning"
author_profile: true
header:
  image: "/images/culture.png"
---

# Currently Working on Deep Learning Project!

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/wip.png" alt="text, previz, deeplearning" width="1500" height="1500">
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
