---
layout: page
title: Posty
---
<h1>Latest Posts<br /></h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.permalink }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>