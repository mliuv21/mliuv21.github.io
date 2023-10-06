---
layout: page
permalink: /projects/
title: Projects
description:
nav: true
nav_order: 1
---
<!-- _pages/projects.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div>
