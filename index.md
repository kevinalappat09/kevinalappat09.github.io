---
layout: default
title: "Welcome to My Blog"
---

<h1 class="text-4xl font-bold text-center mb-8">Welcome to My Blog</h1>

<!-- Categories Section -->
<h2 class="text-3xl font-semibold text-white mb-4">Categories</h2>
<div class="space-y-8">
  {% assign categories = site.categories %}
  
  <!-- Loop through each category -->
  {% for category in categories %}
    <div class="category-section">
      <h3 class="text-2xl font-bold text-white">{{ category[0] }}</h3>
      <ul class="space-y-4">
        
        <!-- Loop through posts in each category -->
        {% for post in category[1] %}
          <li>
            <a href="{{ post.url | relative_url }}" class="text-lg text-gray-300 hover:text-gray-400">
              {{ post.title }}
            </a>
            <p class="text-sm text-gray-500">{{ post.date | date: "%B %d, %Y" }}</p>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>
