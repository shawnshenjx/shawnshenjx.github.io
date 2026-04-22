---
layout: archive
title: "Teaching"
permalink: /teaching/
---

{% assign sorted = site.teaching | sort: 'date' | reverse %}
<ul class="item-list">
{% for post in sorted %}
<li class="item">
  <div class="item-title"><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title | remove: '"' }}</a></div>
  <div class="item-meta">
    {% if post.type %}{{ post.type }}<span class="sep">·</span>{% endif %}
    {% if post.venue %}{{ post.venue }}<span class="sep">·</span>{% endif %}
    {% if post.location %}{{ post.location }}<span class="sep">·</span>{% endif %}
    {{ post.date | date: "%B %Y" }}
  </div>
  {% if post.content and post.content != "" %}
    <div class="item-desc">{{ post.content | strip_html | truncatewords: 40 }}</div>
  {% endif %}
</li>
{% endfor %}
</ul>
