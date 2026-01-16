---
layout: default
title: Archive
permalink: /archive/
---

<article class="post">
  <header class="post-header">
    <h1 class="post-title">Archive</h1>
    <p class="post-meta">
      <span class="post-date">{{ site.posts | where: "published", true | size }} posts in total</span>
    </p>
  </header>

  <div class="post-content">
    {% assign published_posts = site.posts | where: "published", true %}
    
    {% if published_posts.size == 0 %}
    <p style="color: var(--text-tertiary);">No posts yet.</p>
    {% else %}
      {% assign posts_by_year = published_posts | group_by_exp: "post", "post.date | date: '%Y'" %}
      
      {% for year in posts_by_year %}
      <div class="archive-year">
        <h2>{{ year.name }}</h2>
        <ul class="archive-list">
          {% for post in year.items %}
          <li class="archive-item">
            <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %d" }}</time>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            {% if post.tags %}
            <div class="archive-tags">
              {% for tag in post.tags %}
              <span class="post-tag">#{{ tag }}</span>
              {% endfor %}
            </div>
            {% endif %}
          </li>
          {% endfor %}
        </ul>
      </div>
      {% endfor %}
    {% endif %}
  </div>
</article>

<div class="mt-4 text-center">
  <a href="{{ '/' | relative_url }}">← Back to Home</a>
</div>
