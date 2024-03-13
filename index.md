---
layout: base
title: Programmation
---

<div class="home">
  {%- if page.title -%}
    <h1 class="page-heading">{{ page.title }} {{ site.time | date: '%Y' }}</h1>
  {%- endif -%}


  {% if site.paginate %}
    {% assign events = paginator.events %}
  {% else %}
    {% assign events = site.events %}
  {% endif %}


  {%- if events.size > 0 -%}
    {%- if page.list_title -%}
      <h2 class="event-list-heading">{{ page.list_title }}</h2>
    {%- endif -%}
    <ul class="event-list">
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
      {%- for event in events -%}
      <li>
        <span class="event-meta">du {{ event.date_debut | date: date_format }} au {{ event.date_fin | date: date_format }}</span>
        <h3>
          <a class="event-link" href="{{ event.url | relative_url }}">
            {{ event.titre | escape }}
          </a>
        </h3>
        {%- if site.show_excerpts -%}
          {{ event.excerpt }}
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>

    {% if site.paginate %}
      <div class="pager">
        <ul class="pagination">
        {%- if paginator.previous_page %}
          <li><a href="{{ paginator.previous_page_path | relative_url }}" class="previous-page">{{ paginator.previous_page }}</a></li>
        {%- else %}
          <li><div class="pager-edge">•</div></li>
        {%- endif %}
          <li><div class="current-page">{{ paginator.page }}</div></li>
        {%- if paginator.next_page %}
          <li><a href="{{ paginator.next_page_path | relative_url }}" class="next-page">{{ paginator.next_page }}</a></li>
        {%- else %}
          <li><div class="pager-edge">•</div></li>
        {%- endif %}
        </ul>
      </div>
    {%- endif %}

  {%- endif -%}

</div>