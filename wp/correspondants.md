---
---
{% assign correspondants = site.data.membres | where: "position", "Correspondant" %}

# Liste des correspondants des clubs

Club | Nom | Portable | Email
---|---|---|---
{% for correspondant in correspondants -%}
{{correspondant.club}} | {{correspondant.nom}} | {{correspondant.portable}} | {{correspondant.email}} |
{% endfor -%}