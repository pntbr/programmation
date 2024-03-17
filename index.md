---
layout: base
title: Programmation
description: >
  Découvrez le programme annuel des ateliers et animations de l'association Terre Pure, située à Soulan (09). Parcourez à votre rythme les diverses activités proposées, toutes proposées pour enrichir le corps et l'esprit. Joignez-vous à nous pour partager des moments de découverte et de convivialité.
list_title: Stage et ateliers
---

<div class="home">
  <h1 class="page-heading">Programmation {{ site.time | date: '%Y' }}</h1>
  <p class="description">{{ page.description }}</p>

  {% assign events = site.events %}
  {%- if events.size > 0 -%}
    <h2 class="event-list-heading">{{ page.list_title }}</h2>

      {%- assign date_format = site.minima.date_format | default: "%d/%m" -%}
      {%- for event in events -%}
      <article class="event">
        <h3>
          <a class="stage-link" href="{{ event.url | relative_url }}">
            {{ event.titre | escape }}
          </a>
        </h3>
        <span class="stage-meta text-sm">du {{ event.date_debut | date: date_format }} au {{ event.date_fin | date: date_format }}</span>
        <span class="stage-meta text-sm">{{event.categorie}}</span>
        <hr class="hr-half">
        {{ event.excerpt }}
        <hr class="hr-half">
        <section class="stage-animatrice text-sm">
          <figure class="stage-animatrice-pic" role="group">
            <img src="{{ "assets/animatrices/" | append: event.image_animatrice | relative_url }}" alt="{{ event.nom_animatrice }}">
            <figcaption class="sr-only">{{ event.nom_animatrice }}</figcaption>
          </figure>
          <h3 class="stage-animatrice-nom">
            <span class="text-xs">Animé par</span>
            <em>{{ event.nom_animatrice }}</em>
          </h3>
          <p class="stage-animatrice-bio">
            {{ event.bio_animatrice }}
          </p>
        </section>
      </article>
      <hr>
      {%- endfor -%}
  {%- endif -%}

</div>