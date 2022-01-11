---
---
{% assign arbitres = site.data.membres | where: "position", "Arbitre" %}

# Liste des arbitres des clubs

Club | Nom | Portable | Email
---|---|---|---
{% for arbitre in arbitres -%}
{{arbitre.club}} | {{arbitre.nom}} | {{arbitre.portable}} | {{arbitre.email}} |
{% endfor -%}