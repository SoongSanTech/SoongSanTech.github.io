---
layout: page
title: R&D
icon: fas fa-flask
order: 1
---

## Research & Development

Here are the posts related to our R&D activities.

<ul>
  {% for post in site.categories.R&D %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <p>{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
    </li>
  {% endfor %}
</ul>

{% if site.categories.R&D == nil %}
<p>No R&D posts yet. Stay tuned!</p>
{% endif %}
