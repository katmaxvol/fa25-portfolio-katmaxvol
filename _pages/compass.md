---
layout: default
title: Kat Volkova - About Me
permalink: /compass/
---

<div class="project-grid">
  {% assign compass_pages = site.compass | sort: "order" %}
  {% for page in compass_pages %}
    <a class="project-card" href="{{ page.url | relative_url }}">
      <h2>{{ page.title }}</h2>
    </a>
  {% endfor %}
</div>
