---
---
{% assign presidents = site.data.membres | where: "position", "President" %}

# Liste des presidents des clubs

Club | Nom | Portable | Email
---|---|---|---
{% for president in presidents -%}
{{president.club}} | {{president.nom}} | {{president.portable}} | {{president.email}} |
{% endfor -%}