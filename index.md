---
layout: base
title: Programmation
---

<div class="home">
  {%- if page.title -%}
    <h1 class="page-heading">{{ page.title }} {{ site.time | date: '%Y' }}</h1>
  {%- endif -%}

  {% assign events = site.events %}

  {%- if events.size > 0 -%}
    <h2 class="event-list-heading">{{ page.list_title }}</h2>
    <ul class="event-list">
      {%- assign date_format = site.minima.date_format | default: "%d/%m" -%}
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

  {%- endif -%}

</div>