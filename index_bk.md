---
layout: default
title: Home
---

<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
  {% assign projects = site.posts | group_by_exp:"post", "post.project.title" %}

  {% for project in projects %}
    {% assign project_data = project.items[0].project %}
    <section class="py-6 px-4 rounded-lg">
      <h3 class="text-lg font-roboto underline" style="color: #171717; text-decoration-color: #171717"><span class="px-2" style="background-color: {{ project_data.color }};">{{ project_data.title }}</span></h3>
      <p class="text-sm font-open-sans italic" style="color:#d4d4d4">{{ project_data.description }}</p>
      <ul class="hyphen-list mt-2">
        {% for post in project.items %}
          <li><a href="{{ post.url }}" class="text-white hover:text-gray-300">{{ post.title }}</a></li>
        {% endfor %}
      </ul>
    </section>
  {% endfor %}
</div>
