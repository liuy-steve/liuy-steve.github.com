---
layout: page
title: Home page
tagline: Supporting tagline
---
{% include JB/setup %}

    
## My Posts

This blog contains few posts such as...

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



