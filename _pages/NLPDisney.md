---
layout: archive
permalink: /disney_nlp/
title: "Disney Parks Twitter NLP"
author_profile: true
header:
  image: "/images/sf.jpg"
---

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
