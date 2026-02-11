---
layout: page
title: Galleries
permalink: /galleries
---

<div class="gallery-grid">
{% for gallery in site.galleries %}
    <div style="text-align: center;">
        <a href="{{ gallery.url | relative_url }}" class="gallery-grid-item">
            {% if gallery.thumbnail %}
                <img src="{{ gallery.thumbnail | relative_url }}" alt="{{ gallery.title }}">
            {% elsif gallery.images %}
                <img src="{{ gallery.images[0].url | relative_url }}" alt="{{ gallery.title }}">
            {% endif %}
        </a>
        <h3 style="margin-top: 0.5rem;">{{ gallery.title }}</h3>
    </div>
{% endfor %}
</div>
