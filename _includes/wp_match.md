{% include wp_data.md %}

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
{% if match.arbitre2 -%}
{%   assign arbitre = match.arbitre1 | append: ', ' | append: match.arbitre2 -%}
{% else -%}
{%   assign arbitre = match.arbitre1 -%}
{% endif -%}
{% if match.score_locaux -%}
{%   assign score = '<span class="text-nowrap" style="white-space:nowrap">' | append: match.score_locaux | append: '&nbsp;-&nbsp;' | append: match.score_visiteurs | append: '</span>' -%}
{% else -%}
{%   assign score = ' ' -%}
{% endif -%}
{% if match.nul -%}
  {% assign score = score | append: ' <span style="color:red">[TAB]</span>' -%}
{% endif -%}
{{date}} | {{heure}} | {{match.journee}} | {{match.numero}} | {{match.locaux}} | {{score}} | {{match.visiteurs}} | {{match.poule}} | {{arbitre}}
{% endfor -%}
