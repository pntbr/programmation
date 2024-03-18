---
layout: base
title: Programmation
description: >
  Découvrez le programme annuel des ateliers et animations de l'association Terre Pure, située à Soulan (09). Parcourez à votre rythme les diverses activités proposées, toutes proposées pour enrichir le corps et l'esprit. Joignez-vous à nous pour partager des moments de découverte et de convivialité.
list_title: Stage et ateliers
---

<div class="home">
  <h1 class="page-heading"> Programmation {{ site.time | date: '%Y' }}</h1>
  <p class="description">{{ page.description }}</p>

  {% assign events = site.events | sort: "date_debut" %}
  {%- if events.size > 0 -%}
    <h2 class="event-list-heading">{{ page.list_title }}</h2>

      {%- assign date_format = site.minima.date_format | default: "%d/%m" -%}
      {%- for event in events -%}
        {% include event.html event=event %}
      {%- endfor -%}
  {%- endif -%}

</div>