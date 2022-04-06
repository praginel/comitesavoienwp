{% include wp_data.md %}

{% assign teams = "" | split: "," %}
{% for match in matches -%}
{%   assign teams = teams | push: match.locaux %}
{% endfor %}
{% assign teams = teams | uniq %}

<div class="datatable-begin-rankings"></div>

Poule | Position | &Eacute;quipe | Points | Joués | Victoires | Défaites | Nuls | Buts pour | Buts contre | Différence de buts
---|---|---|---|---|---|---|---|---|---
{% for team in teams -%}
{%   include wp_scores.md team=team -%}
{%   assign difference_de_buts = buts_pour | minus: buts_contre -%}
{{poule}} | 0 | {{team}} | {{points}} | {{played}} | {{victories}} | {{defeats}} | {{draws}} | {{buts_pour}} | {{buts_contre}} | {{difference_de_buts}}
{% endfor %}

<div class="datatable-end-rankings"></div>
