---
---
{% assign membres = site.data.membres | sort: "club" %}

# Liste des membres des clubs

Club | Nom | Portable | Email
---|---|---|---
{% for membre in membres -%}
{{membre.club}} | {{membre.position}} | {{membre.nom}} | {{membre.portable}} | {{membre.email}} |
{% endfor -%}