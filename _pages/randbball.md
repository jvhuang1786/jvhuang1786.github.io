---
layout: archive
permalink: /nba_salaries/
title: "Basketball Salaries"
author_profile: true
header:
  image: "/images/warrior.png"
---

# NBA Salaries Analysis

* Below is the slide deck
    * This project was done with R
    * The goal was to try to find out which statistics contributed most to player salary.
    * Useful in classifying a range of salaries in contract negotiations

    * Libraries
        * library(dplyr)
        * library(ggplot2)
        * library(ggrepel)
        * library(directlabels)
        * library(gridExtra)
        * library(tidyr)
        * library(stringr)
        * library(data.table)
        * library(rvest)
        * library(beepr)

      * Salaries and information was webscrapped from various sources.  
        * Salaries from HoopsHype
        * Stats from Patricia Bender

      * Data was collected for the 1999/2000 to 2017/2018 NBA seasons

*Sample Websrapping Code for Salaries*

```r
salary_2019 <- read_html("https://hoopshype.com/salaries/players/") %>%
  html_nodes("table") %>%  html_table

options(max.print=1000000)

# salary_2000_2018 <- lapply(paste0("https://hoopshype.com/salaries/players/", 2000-2001:2017-2018),
#                            function(url){
#                              url %>% read_html() %>%
#                                html_nodes("table") %>%  html_table
#                            })
salary_2018 <- read_html("https://hoopshype.com/salaries/players/2017-2018/") %>%
  html_nodes("table") %>%  html_table

salary_2017 <- read_html("https://hoopshype.com/salaries/players/2016-2017/") %>%
  html_nodes("table") %>%  html_table

salary_2016 <- read_html("https://hoopshype.com/salaries/players/2015-2016/") %>%
  html_nodes("table") %>%  html_table

beep("mario")
```

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-01.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-02.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-03.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-04.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-05.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-06.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-07.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-08.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-09.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-10.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-11.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-12.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-13.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-14.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part1/nba_moneyball_part1-15.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-01.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-02.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-03.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-04.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-05.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-06.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-07.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-08.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-09.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-10.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-11.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-12.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-13.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-14.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-15.png" alt="nba, r" width="1000" height="1000">

<img src="{{ site.url }}{{ site.baseurl }}/images/nba_moneyball_part2/nba_moneyball_part2-16.png" alt="nba, r" width="1000" height="1000">


[Full NBA salaries report](https://nbviewer.jupyter.org/github/jvhuang1786/CapStoneSpringBoard/blob/master/Final%20Report/nba_salary_final_report.html)


[Link to Github](https://github.com/jvhuang1786/CapStoneSpringBoard)

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag| slugify }}" class ="archive_subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
