{% if page contains "poule_exp" %}
{%   assign filter = "item.poule contains '" | append: page.poule_exp | append: "'" %}
{%   assign matches = site.data.n3-2022 | where_exp: "item", filter %}
{%   assign poule_desc = page.poule_exp %}
{% else %}
{%   assign matches = site.data.n3-2022 | where: "poule", page.poule %}
{%   assign poule_desc = page.poule %}
{% endif %}