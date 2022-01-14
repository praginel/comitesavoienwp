---
---
{% if page contains "position" %}
{%   assign filter = "item.position contains '" | append: page.position | append: "'" %}
{%   assign membres = site.data.membres | where_exp: "item", filter %}
{% else %}
{%   assign membres = site.data.membres | sort: "club" %}
{% endif %}

Derni&egrave;re mise &agrave; jour le :
    {{ page.last_modified_at | date: '%Y-%m-%d %H:%M' }}

Club | {% unless page contains "position" %}Position |{% endunless %} Nom | Portable | Email
---|{% unless page contains "position" %}---|{% endunless %}---|---|---
{% for membre in membres -%}
{% capture email %}<a href="mailto:{{membre.email}}">{{membre.email}}</a>{% endcapture -%}
{{membre.club}} | {% unless page contains "position" %}{{membre.position}} |{% endunless %}{{membre.nom}} | {{membre.portable}} | {{membre.email}} |
{% endfor -%}