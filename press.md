---
layout: page
title: 자료실
permalink: /press/
---

보도블록·투수블록·콘크리트 블록에 관한 **기사·방송·보도자료·영상·연구·법령·제도 원문**을 한자리에 모읍니다.

**가감 없이 모읍니다.** 업계에 불리한 것을 빼면 이 목록은 홍보물이 됩니다.
한 줄 설명은 제가 붙인 것이고, 판단은 링크를 열어 직접 하시면 됩니다.
빠진 것이 있으면 알려 주십시오 — 채워 넣겠습니다.

{% assign all = site.data.press.items | concat: site.data.press.sources %}
{% assign types = "방송,기사,연구,법령·고시,제도원문" | split: "," %}

<p class="pressfilter">
  <span>종류</span>
  {% for t in types %}{% assign n = all | where: "type", t | size %}{% if n > 0 %}<a href="#type-{{ forloop.index }}">{{ t }} <em>{{ n }}</em></a>{% endif %}{% endfor %}
</p>

{% for t in types %}
{% assign rows = all | where: "type", t | sort: "date" | reverse %}
{% if rows.size > 0 %}
<h2 id="type-{{ forloop.index }}">{{ t }} <span class="catcount">{{ rows | size }}</span></h2>
<ul class="press">
{% for it in rows %}
  <li>
    <p class="press__meta">
      <time>{{ it.date }}</time>
      <span class="press__outlet">{{ it.outlet }}</span>
      {% if it.tag %}<span class="press__tag press__tag--{{ it.tag }}">{{ it.tag }}</span>{% endif %}
    </p>
    <h3 class="press__title"><a href="{{ it.url }}" target="_blank" rel="noopener noreferrer">{{ it.title }}</a></h3>
    {% if it.note %}<p class="press__note">{{ it.note }}</p>{% endif %}
  </li>
{% endfor %}
</ul>
{% endif %}
{% endfor %}

<p class="press__foot">
목록은 <code>_data/press.yml</code> 에 있습니다. 갱신 {{ site.data.press.updated }} ·
모두 {{ all | size }}건.<br>
제보·추가 요청은 저장소 이슈로 남겨 주시면 확인합니다.
</p>
