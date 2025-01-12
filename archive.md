---
layout: page
title: Blog Archive
---

{% for tag in site.tags %}
  <h4>{{ tag[0] }}</h4>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</font></li>
    {% endfor %}
  </ul>
{% endfor %}
