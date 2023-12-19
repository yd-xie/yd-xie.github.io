---
layout: page
permalink: /news/
title: News
description: News by categories in reversed chronological order.
nav: true
nav_order: 1
---
<!-- _pages/news.md -->

<div class="news">
{% if site.news != blank -%}
{%- assign news_size = site.news | size -%}
<div class="table-responsive" {% if include.limit and site.announcements.scrollable and news_size > 3 %}style="max-height: 60vw"{% endif %}>
    <table class="table table-sm table-borderless table-hover">
    {%- assign news = site.news | reverse -%}
    {% if include.limit and site.announcements.limit %}
    {% assign news_limit = site.announcements.limit %}
    {% else %}
    {% assign news_limit = news_size %}
    {% endif %}
    {% for item in news limit: news_limit %}
    <tr>
        <th scope="row" style="width: 20%">{{ item.date | date: "%b %-d, %Y" }}</th>
        <td>
        {% if item.inline -%}
            {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
        {%- else -%}
            <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
        {%- endif %}
        </td>
    </tr>
    {%- endfor %}
    </table>
</div>
{%- else -%}
<p>No news so far...</p>
{%- endif %}
</div>