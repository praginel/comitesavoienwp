{% assign pour = include.pour | plus: 0 -%}
{% assign contre = include.contre | plus: 0 -%}
{% if pour > contre -%}
{%   assign victories = victories | plus: 1 -%}
{%   assign points = points | plus: 2 -%}
{% elsif pour < contre -%}
{%   assign defeats = defeats | plus: 1 -%}
{% else -%}
{%   assign draws = draws | plus: 1 -%}
{%   assign points = points | plus: 1 -%}
{% endif -%}
{% assign played = played | plus: 1 -%}
{% assign buts_pour = buts_pour | plus: pour -%}
{% assign buts_contre = buts_contre | plus: contre -%}