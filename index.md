---
layout: base
title: Programmation
---

<style>

  img {
    width: 100px;
    height: auto;
  }

  hr {
    height: 0;
    margin: 1.6em 0;
    padding: 0;
    border: 0;
    border-bottom-width: 0px;
    border-bottom-style: none;
    border-bottom-color: currentcolor;
    border-bottom: 1px solid #e5e7ea;
  }

  .text-xs {
    font-size: .75em;
  }

  .text-sm {
    font-size: .875em;
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    overflow: hidden;
    border: 0;
    white-space: nowrap;
    clip: rect(0 0 0 0);
    -webkit-clip-path: inset(50%);
    clip-path: inset(50%);
  }

  .stage-animatrice-nom {
    line-height: 1.25;
  }

  .stage-animatrice-pic {
    max-width: 6em;
    float: left;
    margin: .5em 1em 0 0;
    overflow: hidden;
    border-radius: 50%;
  }
</style>

<div class="home">
  <h1 class="page-heading">Programmation {{ site.time | date: '%Y' }}</h1>

  {% assign events = site.events %}

  {%- if events.size > 0 -%}
    <h2 class="event-list-heading">{{ page.list_title }}</h2>

      {%- assign date_format = site.minima.date_format | default: "%d/%m" -%}
      {%- for event in events -%}
      <article>
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
      </article>
      <hr>
      {%- endfor -%}
  {%- endif -%}

</div>