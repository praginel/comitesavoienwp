---
---
{% if page contains "categorie" %}
{%   assign filter = "item.categorie contains '" | append: page.categorie | append: "'" %}
{%   assign competitions = site.data.natation-2022 | where_exp: "item", filter %}
{% else %}
{%   assign competitions = site.data.natation-2022 | sort: "start_date" %}
{% endif %}

{% if page contains "last_modified_at" -%}
Derni&egrave;re mise &agrave; jour le :
    {{ page.last_modified_at | date: '%Y-%m-%d %H:%M' }}
{% else %}
    {% include maj.md %}
{% endif %}

Date | Catégorie | Intitulé de la Compétition | Lieu | Programme | Programme Détailé | Résultats
---|---|---|---|---|---|---
{% for competition in competitions -%}
{% if competition.date_fin != null && competition.date_fin != competition.date_debut -%}
  {% assign date = competition.date_debut | append: ' au ' | append: competition.date_fin -%}
{% else -%}
{%   assign date = competition.date_debut -%}
{% endif -%}
{% if competition.programme != null -%}
  {% assign programme = "<a href=\"> " | append: competition.programme | append: "\">" | append: competition.programme | append: "</a>" -%}
{% else -%}
{%   assign programme = ' ' -%}
{% endif -%}
{% if competition.programme_detaille != null -%}
  {% assign programme_detaille = "<a href=\"> " | append: competition.programme_detaille | append: "\">" | append: competition.programme_detaille | append: "</a>" -%}
{% else -%}
{%   assign programme_detaille = ' ' -%}
{% endif -%}
{% if competition.resultats != null -%}
  {% assign resultats = "<a href=\"> " | append: competition.programme_detaille | append: "\">" | append: competition.resultats | append: "</a>" -%}
{% else -%}
{%   assign resultats = ' ' -%}
{% endif -%}
{{date}} | {{competition.categorie}} | {{competition.intitule}} | {{competition.lieu}} | {{programme}} | {{programme_detaille}} | {{resultats}}
{% endfor -%}
