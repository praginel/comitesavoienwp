---
---
{% assign entraineurs = site.data.membres | where_exp: "item", "item.position contains 'Entraineur'" %}

# Liste des entraineurs des clubs

Club | Type | Nom | Portable | Email
---|---|---|---
{% for entraineur in entraineurs -%}
{{entraineur.club}} | {{entraineur.position}} | {{entraineur.nom}} | {{entraineur.portable}} | {{entraineur.email}} |
{% endfor -%}