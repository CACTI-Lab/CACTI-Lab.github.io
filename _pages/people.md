---
layout: page
title: people
permalink: /people/
description: members of the group
nav: true
nav_order: 2
display_categories: [current, alumni]
horizontal: false
---
<div class="alert alert-success" role="alert">
  We are recruiting students for Spring '25. [Apply here](https://tinyurl.com/cactilab) or on HMC's URO (not both). Positions are only open to 5C students.
</div>

Any open positions will be posted on Harvey Mudd's URO portal (usually in August/November) or on the [HMC CS page for summer research opportunities](https://www.hmc.edu/cs/research/reu/) (usually in January).

Please note: there are currently no available positions for graduate students.

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <!-- <a id="{{ category }}" href=".#{{ category }}"> -->
    <h2 class="category">{{ category }}</h2>
  <!-- </a> -->
  {% assign categorized_projects = site.people | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.people | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
