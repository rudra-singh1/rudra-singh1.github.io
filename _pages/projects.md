---
layout: page
title: photography
permalink: /projects/
description: Some neat pictures I've taken over the years.
nav: true
nav_order: 3
---

<div style="text-align: center;">
  <!-- 1st smaller full width -->
  <img src="/assets/img/teaching/first.png"
       alt="Teaching 1"
       style="width: 80%; height: auto; margin: 20px 0;" />

  <!-- 2nd smaller full width -->
  <img src="/assets/img/teaching/second.png"
       alt="Teaching 2"
       style="width: 80%; height: auto; margin: 20px 0;" />

  <!-- 3rd + 4th side by side -->
  <div style="display: flex; justify-content: center; gap: 20px; margin: 20px 0;">
    <img src="/assets/img/teaching/third.png"
         alt="Teaching 3"
         style="width: 45%; height: auto;" />
    <img src="/assets/img/teaching/fourth.png"
         alt="Teaching 4"
         style="width: 45%; height: auto;" />
  </div>

  <!-- 5th smaller full width -->
  <img src="/assets/img/teaching/fifth.png"
       alt="Teaching 5"
       style="width: 80%; height: auto; margin: 20px 0;" />
</div>


<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>f
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

{% assign sorted_projects = site.projects | sort: "importance" %}

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
