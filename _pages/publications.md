---
layout: archive
title: "Publications"
subtitle: "See also my <a href='https://scholar.google.com/citations?user=0-qmmqkAAAAJ&hl=en'>Google Scholar</a>."
permalink: /publications/
---

{% assign sorted = site.publications | sort: 'date' | reverse %}
{% assign years = "" | split: "" %}
{% for post in sorted %}
  {% assign y = post.date | date: "%Y" %}
  {% unless years contains y %}{% assign years = years | push: y %}{% endunless %}
{% endfor %}

{% for year in years %}
<section class="year-group">
  <h2>{{ year }}</h2>
  <ul class="pub-list">
  {% for post in sorted %}
    {% assign py = post.date | date: "%Y" %}
    {% if py == year %}
      {% assign paragraphs = post.content | split: '</p>' %}
      {% assign authors_p = paragraphs[0] | append: '</p>' | strip_html | strip %}
      {% assign desc_p    = paragraphs[1] | append: '</p>' | strip_html | strip %}
    <li class="pub-item">
      <div class="pub-title"><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title | remove: '"' }}</a></div>
      {% if authors_p and authors_p != "" %}<div class="pub-authors">{{ authors_p }}</div>{% endif %}
      {% if post.venue %}<div class="pub-venue">{{ post.venue }}</div>{% endif %}
      {% if desc_p and desc_p != "" %}<div class="pub-excerpt">{{ desc_p }}</div>{% elsif post.excerpt and post.excerpt != "" %}<div class="pub-excerpt">{{ post.excerpt | strip_html | strip_newlines }}</div>{% endif %}
      <div class="pub-links">
        {% if post.paperurl %}<a href="{{ post.paperurl }}">Paper</a>{% endif %}
        <a href="{{ post.url | prepend: site.baseurl }}">Details</a>
      </div>
    </li>
    {% endif %}
  {% endfor %}
  </ul>
</section>
{% endfor %}
