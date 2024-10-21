{% if page contains "position" %}
{%   assign filter = "item.position contains '" | append: page.position | append: "'" %}
{%   assign membres = site.data.membres | where_exp: "item", filter %}
{% else %}
{%   assign membres = site.data.membres | sort: "club" %}
{% endif %}

<div class="datatable-begin"></div>

Club | Position | Nom | Portable | Email
---|---|---|---|---
{% for membre in membres -%}
{% capture email -%}<a href="mailto:{{membre.email}}">{{membre.email}}</a>{% endcapture -%}
{{membre.club}} | {{membre.position}} | {{membre.nom}} | {{membre.portable}} | {{email}}
{% endfor %}

<div class="datatable-end"></div>