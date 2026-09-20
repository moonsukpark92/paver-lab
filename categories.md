---
layout: page
title: 카테고리
permalink: /categories/
---

{% assign cats = "투수·배수,공기정화·기능성,배합·재료,성형·설비,양생·품질,시공·유지관리" | split: "," %}
{% for c in cats %}
  {% assign posts = site.posts | where: "category", c %}
  <h2 id="{{ c | slugify }}">{{ c }} <span class="catcount">{{ posts | size }}</span></h2>
  {% if posts.size == 0 %}
  <p class="catempty">아직 글이 없습니다.</p>
  {% else %}
  <ul class="notes notes--compact">
  {% for p in posts %}
    <li class="note">
      <p class="note__meta"><span class="chip chip--quiet">{{ p.grade }}</span>
        <time datetime="{{ p.date | date_to_xmlschema }}">{{ p.date | date: "%Y.%m.%d" }}</time></p>
      <h3 class="note__title"><a href="{{ p.url | relative_url }}">{{ p.title }}</a></h3>
      {% if p.excerpt_text %}<p class="note__lede">{{ p.excerpt_text }}</p>{% endif %}
    </li>
  {% endfor %}
  </ul>
  {% endif %}
{% endfor %}
