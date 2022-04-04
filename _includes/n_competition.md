{% if page contains "categorie" %}
{%   assign filter = "item.categorie contains '" | append: page.categorie | append: "'" %}
{%   assign competitions = site.data.natation-2022 | where_exp: "item", filter %}
{% else %}
{%   assign competitions = site.data.natation-2022 %}
{% endif %}

| Date | Catégorie | Intitulé de la Compétition | Lieu | Programme | Programme Détailé | Résultats |
| --- | --- | --- | --- | --- | --- | --- |
{% for competition in competitions -%}
{% if competition.date_debut == null -%}
||||<span style="background-color:cyan">**{{competition.intitule}}**</span>|||
{% else -%}
{% if competition.date_fin != null && competition.date_fin != competition.date_debut -%}
{%   assign date = competition.date_debut | append: ' au ' | append: competition.date_fin -%}
{% else -%}
{%   assign date = competition.date_debut -%}
{% endif -%}
{% case competition.categorie -%}
{% when null -%}
{%   assign categorie = '' -%}
{% when 'Jeunes', 'Jeunes et +', 'Jeunes 3 et +' -%}
{%   assign categorie = '<span style="background-color:green; color:white">' | append: competition.categorie | append: '</span>' -%}
{% when 'Avenirs' -%}
{%   assign categorie = '<span style="background-color:purple; color:white">' | append: competition.categorie | append: '</span>' -%}
{% else -%}
{%   assign categorie = competition.categorie -%}
{% endcase -%}
{% if competition.programme != null -%}
{%   assign programme = competition.programme -%}
{% else -%}
{%   assign programme = '' -%}
{% endif -%}
{% if competition.programme_detaille != null -%}
{%   assign programme_detaille = competition.programme_detaille -%}
{% else -%}
{%   assign programme_detaille = '' -%}
{% endif -%}
{% if competition.resultats != null -%}
{%   assign resultats = competition.resultats -%}
{% else -%}
{%   assign resultats = '' -%}
{% endif -%}
| {{date}} | {{categorie}} | {{competition.intitule}} | {{competition.lieu}} |{{programme}}|{{programme_detaille}}|{{resultats}}|
{% endif -%}
{% endfor -%}
