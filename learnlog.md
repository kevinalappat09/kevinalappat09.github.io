---
layout: default
title: Weekly Learn Log
permalink: /learnlog/
---

<h1>Weekly Learn Log</h1>
<p>A log of everything new I learnt over the week</p>
<br>
<ul>
    {% for log in site.learnlogs %}
        <li>
            <a href="{{ log.url }}">{{ log.title }}</a> — {{ log.date | date: "%b %-d, %Y" }}
        </li>
    {% endfor %}
</ul>