---
layout: default
title: Projelerim
permalink: /my-projects/bilgisayar-terimleri-sozlugu
---

<nav>
      <ul style="display: flex;list-style:none">
        {% for item in site.data.menu %}
        <li style="margin-right: 50px"><a style="text-decoration:none" class="{% if page.url == item.link %}active{% endif %}" href="{{ item.link }}">{{ item.title }}</a></li>
        {% endfor %}
      </ul>
</nav>

## My Projects

Bu kısımda github'daki projelerimi açıklayacağım.

Projenin Github sayfasına gitmek için aşağıdaki butona basıp gidebilirsiniz.

<button style="background-color: white;color: black;border: 2px solid #4CAF50;width: 250px">Kodun tam haline gitmek için Tiklayiniz</button>

---

<footer style="float:left;"><small>&copy; 2022 thealper2</small></footer>
<footer style="float:right;"><small><a href="https://github.com/thealper2">My Github</a></small></footer>