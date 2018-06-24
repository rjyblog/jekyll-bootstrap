---
layout: page
title: Jason's Blog
tagline: 任建勇的博客
---
{% include JB/setup %}

求知若饥，虚心若愚。

## 文章更新

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
