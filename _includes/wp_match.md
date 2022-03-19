---
---
{% if page contains "poule_exp" %}
{%   assign filter = "item.poule contains '" | append: page.poule_exp | append: "'" %}
{%   assign matches = site.data.n3-2022 | where_exp: "item", filter %}
{% else %}
{%   assign matches = site.data.n3-2022 | where: "poule", page.poule %}
{% endif %}

Date | Heure | Journée | Match | Club Receveur | Score | Club Visiteur | Poule | Arbitres
---|---|---|---|---|---|---|---|---
{% for match in matches -%}
{% if match.date_modifiee == 'y' -%}
  {% assign date = '<span style="color:red">' | append: match.date | append: '</span>' -%}
{% else -%}
{%   assign date = match.date -%}
{% endif -%}
{% if match.heure_modifiee == 'y' -%}
{%   assign heure = '<span style="color:red">' | append: match.heure | append: '</span>' -%}
{% else -%}
{%   assign heure = match.heure -%}
{% endif -%}
{% if match.arbitre2 != null -%}
{%   assign arbitre = match.arbitre1 | append: ', ' | append: match.arbitre2 -%}
{% else -%}
{%   assign arbitre = match.arbitre1 -%}
{% endif -%}
{% if match.score_locaux != null -%}
{%   assign score = match.score_locaux | append: '&nbsp;-&nbsp;' | append: match.score_visiteurs -%}
{% else -%}
{%   assign score = ' ' -%}
{% endif -%}
{{date}} | {{heure}} | {{match.journee}} | {{match.numero}} | {{match.locaux}} | {{score}} | {{match.visiteurs}} | {{match.poule}} | {{arbitre}}
{% endfor -%}
