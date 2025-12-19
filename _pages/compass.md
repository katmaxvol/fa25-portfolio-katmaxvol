---
layout: default
title: Kat Volkova - About Me
permalink: /compass/
---

<div class="project-grid">
  {% assign pages = site.compass | sort: "order" %}
  {% for page in pages %}
    <a class="project-card" href="{{ page.url | relative_url }}">
      <h2>{{ page.title }}</h2>
    </a>
  {% endfor %}
</div>
