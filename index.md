---
layout: default
---
En gång i tiden fanns denna lista på Kaffebryggan.com som numer enbart är nåbar via web.archive.org. [PRs are welcome - help us fill the blanks (❓)!](https://github.com/svenska-kafferosterier-rymdvarel-se/svenska-kafferosterier-rymdvarel-se.github.io)

{% assign loops = "main,eol" | split: "," %}
{% for loop in loops %}
  {% if loop == "eol" %}
### EOL
  {% endif %}
<table>
  <tr>
    <th>Namn</th>
    <th>Plats (📍)</th>
    <th>URL (🌐)</th>
    <th>Webshop (📦)</th>
    <th>Prenumeration (🗓)</th>
    <th>Café/bar (☕️)</th>
    <th>Kurser (🧑‍🎓)</th>
    <th>Kommentar (💬)</th>
  </tr>
  {% for entry in site.data.roasters %}
    {% if loop == "main" and entry.eol %}
      {% continue %}
    {% endif %}

    {% if loop == "eol" and entry.eol != true %}
      {% continue %}
    {% endif %}

    {% if entry.eol %}
  <tr class="strikeout">
    {% else %}
  <tr>
    {% endif %}
    <td>{{ entry.name }}</td>
    {% if entry.location %}
    <td>{{ entry.location }}</td>
    {% else %}
    <td>❓</td>
    {% endif %}
    <td>{{ entry.url | markdownify  }}</td>
    <td>
    {% if entry.webshop != None %}
      {% if entry.webshop == true %}
      📦
      {% else %}
      ❌
      {% endif %}
    {% else %}
      ❓
    {% endif %}
    </td>

    <td>
    {% if entry.subscription != None %}
      {% if entry.subscription == true %}
      🗓
      {% else %}
      ❌
      {% endif %}
    {% else %}
      ❓
    {% endif %}
    </td>

    <td>
    {% if entry.cafe != None %}
      {% if entry.cafe == true %}
      ☕️
      {% else %}
      ❌
      {% endif %}
    {% else %}
      ❓
    {% endif %}
    </td>

    <td>
    {% if entry.courses != None %}
      {% if entry.courses == true %}
      🧑‍🎓
      {% else %}
      ❌
      {% endif %}
    {% else %}
      ❓
    {% endif %}
    </td>

  <td>{{ entry.comment }}</td>
  </tr>
  {% endfor %}
</table>
{% endfor %}
