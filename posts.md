---
layout: page
title: Posts
background: '/img/background/posts/writing.png'
---
<h1>Latest Posts<br /></h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <strong>{% if page.author %}{{ page.author }}{% else %}{{ site.author }}{% endif %} - {{ post.date | date: "%B %e, %Y" }}</strong> 
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>