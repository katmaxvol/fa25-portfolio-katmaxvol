---
layout: default
title: Compass
permalink: /compass/
---

<div class="gallery-container">
  <div class="project-gallery">
    {% assign compass_pages = site.compass | sort: "order" %}
    {% for page in compass_pages %}
      <div class="gallery-item">
        <a href="{{ page.url | relative_url }}">
          {% if page.image %}
            <img src="{{ page.image | relative_url }}" alt="{{ page.title }}" />
          {% endif %}
          <p>{{ page.title }}</p>
        </a>
      </div>
    {% endfor %}
  </div>
</div>
