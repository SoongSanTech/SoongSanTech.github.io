---
layout: page
title: Docs
icon: fas fa-book
order: 2
---

## Documentation

Here are the posts related to our documentation.

<ul>
  {% for post in site.categories.DOCS %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <p>{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
    </li>
  {% endfor %}
</ul>

{% if site.categories.DOCS == nil %}
<p>No documentation posts yet. Stay tuned!</p>
{% endif %}
