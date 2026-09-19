---
layout: page
title: 표준 원장
permalink: /standards/
---

이 연구소가 근거로 삼는 표준 목록입니다. **`확인` 열이 핵심입니다** —
`원문` 은 표준 전문이나 발행기관 문서를 직접 읽고 옮긴 값이고,
`2차` 는 요약·기사·안내 페이지에서 인용한 값입니다. 2차 값은 본문에서 `[미검증]` 으로 표시합니다.

<table>
  <thead><tr><th>표준</th><th>제목</th><th>기관</th><th>확인</th></tr></thead>
  <tbody>
  {% for s in site.data.standards.standards %}
    <tr>
      <td><code>{{ s.id }}</code></td>
      <td>{% if s.source %}<a href="{{ s.source }}">{{ s.title }}</a>{% else %}{{ s.title }}{% endif %}</td>
      <td>{{ s.body }}</td>
      <td>{% if s.verified %}원문{% else %}2차{% endif %}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>

### 기록된 충돌

같은 대상을 두고 값이 갈리는 지점입니다. 한쪽을 지우지 않고 둘 다 남깁니다.

{% for c in site.data.standards.conflicts %}
- **{{ c.topic }}** — {{ c.a }} ↔ {{ c.b }}<br>{{ c.resolution }}
{% endfor %}
