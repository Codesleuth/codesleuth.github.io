---
layout: stackedit
title: NDC Oslo 2015 Notes
permalink: /notes/index.html
---


<ul>
{% for page in site.pages %}{% if page.ndcoslo2015 == true %}
<li>
  <a href="{{ page.url }}"> ({{ page.date | date: '%A %H:%M' }}) {{ page.title }}</a>
</li>
{% endif %}{% endfor %}
</ul>