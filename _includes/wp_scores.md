{% include wp_data.md -%}
{% assign played = 0 -%}
{% assign points = 0 -%}
{% assign victories = 0 -%}
{% assign defeats = 0 -%}
{% assign draws = 0 -%}
{% assign buts_contre = 0 -%}
{% assign buts_pour = 0 -%}
{% for match in matches -%}
{%   if match.score_locaux -%}
{%     if match.locaux == include.team -%}
{%       include wp_scores_match.md pour=match.score_locaux contre=match.score_visiteurs draw=match.nul -%}
{%       assign poule = match.poule -%}
{%     elsif match.visiteurs == include.team -%}
{%       include wp_scores_match.md pour=match.score_visiteurs contre=match.score_locaux draw=match.nul -%}
{%     endif -%}
{%   endif -%}
{% endfor -%}
