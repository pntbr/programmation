---
layout: base
title: Programmation
---

<div class="home">
  <h1 class="page-heading">Programmation {{ site.time | date: '%Y' }}</h1>

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
        <section class="stage-animatrice text-sm">
          <figure class="stage-animatrice-pic" role="group">
            <img src="{{ "assets/animatrices/" | append: event.image_animatrice | relative_url }}" alt="{{ event.nom_animatrice }}">
            <figcaption class="sr-only">{{ event.nom_animatrice }}</figcaption>
          </figure>
          <h3 class="stage-animatrice-nom">
            <span class="text-xs">Présenté par</span>
            <br><!-- TODOUX supprimer ce BR -->
            <em>{{ event.nom_animatrice }}</em>
          </h3>
          <p class="stage-animatrice-bio">
            {{ event.bio_animatrice }}
          </p>
        </section>
         <hr>
        {{ event.animatrice }} <br>
        {%- if site.show_excerpts -%}
          {{ event.excerpt }}
        {%- endif -%}
      </li>
      <hr>
      {%- endfor -%}
    </ul>

  {%- endif -%}

</div>