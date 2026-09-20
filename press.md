---
layout: page
title: 기사 모음
permalink: /press/
---

보도블록·투수블록·콘크리트 블록을 다룬 기사를 모읍니다.
**좋든 싫든 모읍니다** — 업계에 불리한 기사를 빼면 이 목록은 홍보물이 됩니다.

한 줄 설명은 제가 붙인 것이고, 판단은 링크를 열어 직접 하시면 됩니다.
빠진 기사가 있으면 알려 주십시오.

{% assign items = site.data.press.items %}
{% assign tags = "비판,제도,기술,산업" | split: "," %}

<p class="pressfilter">
  <span>분류</span>
  {% for t in tags %}{% assign n = items | where: "tag", t | size %}{% if n > 0 %}<a href="#tag-{{ t }}">{{ t }} <em>{{ n }}</em></a>{% endif %}{% endfor %}
  <a href="#sources">제도 원문 <em>{{ site.data.press.sources | size }}</em></a>
</p>

{% for t in tags %}
{% assign rows = items | where: "tag", t %}
{% if rows.size > 0 %}
<h2 id="tag-{{ t }}">{{ t }} <span class="catcount">{{ rows | size }}</span></h2>
<ul class="press">
{% for it in rows %}
  <li>
    <p class="press__meta"><time>{{ it.date }}</time><span class="press__outlet">{{ it.outlet }}</span></p>
    <h3 class="press__title"><a href="{{ it.url }}" target="_blank" rel="noopener noreferrer">{{ it.title }}</a></h3>
    {% if it.note %}<p class="press__note">{{ it.note }}</p>{% endif %}
  </li>
{% endfor %}
</ul>
{% endif %}
{% endfor %}

<h2 id="sources">제도 원문 <span class="catcount">{{ site.data.press.sources | size }}</span></h2>

기사보다 이쪽이 먼저입니다. 기사는 원문을 요약하면서 값이 흔들립니다.

<ul class="press">
{% for it in site.data.press.sources %}
  <li>
    <p class="press__meta"><time>{{ it.date }}</time><span class="press__outlet">{{ it.outlet }}</span></p>
    <h3 class="press__title"><a href="{{ it.url }}" target="_blank" rel="noopener noreferrer">{{ it.title }}</a></h3>
    {% if it.note %}<p class="press__note">{{ it.note }}</p>{% endif %}
  </li>
{% endfor %}
</ul>

<p class="press__foot">목록은 <code>_data/press.yml</code> 에 있습니다. 갱신: {{ site.data.press.updated }}</p>
