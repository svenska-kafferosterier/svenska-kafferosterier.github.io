---
layout: default
---
En gång i tiden fanns denna lista på Kaffebryggan.com som numer enbart är nåbar via [web.archive.org](https://web.archive.org/web/20210812131008/https://www.kaffebryggan.com/svenska-kafferosterier/). [PRs are welcome - help us fill the blanks (❓)!](https://github.com/svenska-kafferosterier/svenska-kafferosterier.github.io)

<script src="assets/js/sorttable.js"></script>

{% assign loops = "main,eol" | split: "," -%}
{% for loop in loops -%}
  {% if loop == "eol" -%}
### EOL
  {% endif -%}

<table class="sortable">
  <tr>
    <th>Namn</th>
    <th>Plats (📍)</th>
    <th>URL (🌐)</th>
    <th>Webshop (📦)</th>
    <th>Prenumeration (🗓)</th>
    <th>Café/bar (☕️)</th>
    <th>Kurser (🧑‍🎓)</th>
    <th><a href="https://en.wikipedia.org/wiki/Single-origin_coffee">Single Origin</a> (🥇)</th>
    <th>Kommentar (💬)</th>
  </tr>
  {% for entry in site.data.roasters -%}
    {% if loop == "main" and entry.eol -%}
      {% continue -%}
    {% endif -%}

    {% if loop == "eol" and entry.eol != true -%}
      {% continue -%}
    {% endif -%}

    {% if entry.eol -%}
  <tr class="strikeout">
    {% else -%}
  <tr>
    {% endif -%}
    <td>{{ entry.name }}</td>
    {% if entry.location -%}
    <td>{{ entry.location }}</td>
    {% else -%}
    <td>❓</td>
    {% endif -%}
    <td><a href="https://{{ entry.url }}">{{ entry.url }}</a></td>
    <td>
    {% if entry.webshop -%}
    📦
    {% elsif entry.webshop == false -%}
    ❌
    {% else -%}
    ❓
    {% endif -%}
    </td>

    <td>
    {% if entry.subscription -%}
    🗓
    {% elsif entry.subscription == false -%}
    ❌
    {% else -%}
    ❓
    {% endif -%}
    </td>

    <td>
    {% if entry.cafe -%}
    ☕️
    {% elsif entry.cafe == false -%}
    ❌
    {% else -%}
    ❓
    {% endif -%}
    </td>

    <td>
    {% if entry.courses -%}
    🧑‍🎓
    {% elsif entry.courses == false -%}
    ❌
    {% else -%}
    ❓
    {% endif -%}
    </td>

    <td>
    {% if entry.singleorigin -%}
    🥇
    {% elsif entry.singleorigin == false -%}
    ❌
    {% else -%}
    ❓
    {% endif -%}
    </td>

    <td>{{ entry.comment }}</td>
  </tr>
  {% endfor -%}
</table>
{% endfor -%}
