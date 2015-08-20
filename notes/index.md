---
layout: stackedit
title: NDC Oslo 2015 Notes
permalink: /notes/index.html
---

<h1>Wednesday</h1>
<ul>
{% for page in site.pages %}{% if page.ndcoslo2015 == true %}{% assign dayofweek = page.date | date '%w' %}{% if dayofweek == '3' %}
<li>
  <a href="{{ page.url }}">{{ page.date | date: '%H:%M' }}: {{ page.title }}</a>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>

<h1>Thursday</h1>
<ul>
{% for page in site.pages %}{% if page.ndcoslo2015 == true %}{% assign dayofweek = page.date | date '%w' %}{% if dayofweek == '4' %}
<li>
  <a href="{{ page.url }}">{{ page.date | date: '%H:%M' }}: {{ page.title }}</a>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>

<h1>Friday</h1>
<ul>
{% for page in site.pages %}{% if page.ndcoslo2015 == true %}{% assign dayofweek = page.date | date '%w' %}{% if dayofweek == '5' %}
<li>
  <a href="{{ page.url }}">{{ page.date | date: '%H:%M' }}: {{ page.title }}</a>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>