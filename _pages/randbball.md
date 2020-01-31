---
layout: archive
permalink: /nba_salaries/
title: "Basketball Salaries"
author_profile: true
header:
  image: "/images/warrior.png"
---

[R Basketball Salaries Analysis](https://github.com/jvhuang1786/CapStoneSpringBoard)

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag| slugify }}" class ="archive_subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
