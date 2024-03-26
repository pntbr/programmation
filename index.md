---
layout: base
title: Programmation
description: >
  Voici le programme pour l'année des ateliers et animations de l'association Terre Pure, située à Soulan (09). Parcourez-le à votre rythme et joignez-vous à nous pour partager des moments de découverte et de convivialité.
---

<div class="home">
  <h1 class="page-heading">Programmation {{ site.time | date: '%Y' }}</h1>
  <p class="description">{{ page.description }}</p>
  
  {% assign animations = site.animations | sort: "ordre" %}
  {% if animations.size > 0 %}
    <h2 class="event-list-heading">Animations</h2>
    <section class="animations">
      {% for animation in animations %}
          {% include animation.html animation=animation %}
      {% endfor %}
    </section>
  {% endif %}

  {% assign current_date = site.time | date: '%Y-%m-%d' %}
  {% assign events = site.events | sort: "date_debut" %}
  {% if events.size > 0 %}
    <h2 class="event-list-heading">Stage et ateliers</h2>
    <section class="stage-futur">
      <h3>À venir</h3>
      {% for event in events %}
        {% assign end_date = event.date_fin | date: '%Y-%m-%d' %}
        {% if end_date >= current_date %}
          {% include event.html event=event %}
        {% endif %}
      {% endfor %}
    </section>
    <section class="stage-finis">
    <h3>Passés</h3>
      {% for event in events %}
        {% assign end_date = event.date_fin | date: '%Y-%m-%d' %}
        {% if end_date < current_date %}
          {% include event.html event=event %}
        {% endif %}
      {% endfor %}
    </section>
  {% endif %}
</div>
