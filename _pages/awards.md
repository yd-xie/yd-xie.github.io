---
layout: page
permalink: /awards/
title: Awards
description: Awards by categories in reversed chronological order.
nav: true
nav_order: 3
---
<!-- _pages/awards.md -->

<div class="awards">
{% if site.awards != blank -%}
{%- assign awards_size = site.awards | size -%}
<div class="table-responsive" {% if include.limit and site.announcements.scrollable and awards_size > 3 %}style="max-height: 60vw"{% endif %}>
    <table class="table table-sm table-borderless">
    {%- assign awards = site.awards | reverse -%}
    {% if include.limit and site.announcements.limit %}
    {% assign awards_limit = site.announcements.limit %}
    {% else %}
    {% assign awards_limit = awards_size %}
    {% endif %}
    {% for item in awards limit: awards_limit %}
    <tr>
        <th scope="row" style="width: 20%">{{ item.date | date: "%b %-d, %Y" }}</th>
        <td>
        {% if item.inline -%}
            {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
        {%- else -%}
            <a class="awards-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
        {%- endif %}
        </td>
    </tr>
    {%- endfor %}
    </table>
</div>
{%- else -%}
<p>No awards so far...</p>
{%- endif %}
</div>