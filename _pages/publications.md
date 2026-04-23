---
layout: page
permalink: /publications/
title: Publications
description:
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

{% assign publication_years = site.bibliography | map: 'year' | uniq | sort | reverse %}

{%- for y in publication_years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div>
