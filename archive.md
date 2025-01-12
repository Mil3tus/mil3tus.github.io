---
layout: page
title: Blog Archive
---

{% for tag in site.tags %}
  <h4>{{ tag[0] }}</h4>
  <ul>
    {% for post in tag[1] %}
      <li><font size=1><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></font></li>
    {% endfor %}
  </ul>
{% endfor %}
