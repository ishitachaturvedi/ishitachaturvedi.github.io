---
layout: default
permalink: /blog/
title: Blog
nav: true
nav_order: 1
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---

{% block content %}
<ul>
    <li><a href="https://ishitachaturvedi.github.io/blog/2025/Applying-to-gradschool/">My journey into graduate school</a></li>
</ul>
{% endblock %}