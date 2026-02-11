---
layout: page
title: Blog
permalink: /blog
---

<div class="blog-list">
{% for post in site.posts %}
    <div class="blog-post-preview">
        <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
        <p class="date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></p>
        {{ post.excerpt }}
        <a href="{{ post.url | relative_url }}">Read more →</a>
    </div>
{% endfor %}
</div>
