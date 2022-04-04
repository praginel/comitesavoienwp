{% if include.pour > include.contre -%}
{%   assign victories = victories | plus: 1 -%}
{% elsif include.pour < include.contre -%}
{%   assign defeats = defeats | plus: 1 -%}
{% else -%}
{%   assign draws = draws | plus: 1 -%}
{% endif -%}
{% assign played = played | plus: 1 -%}
{% assign buts_contre = buts_contre | plus: include.contre -%}
{% assign buts_pour = buts_pour | plus: include.pour -%}