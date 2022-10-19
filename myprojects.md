---
layout: default
title: Projelerim
permalink: /my-projects/
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

### VTscan

Proje hakkında bilgiler, resim

[VTscan](/my-projects/vtscan)

---

### GTFObins-Script

Proje hakkında bilgiler, resim

[GTFObins-Script](/my-projects/gtfobins-script)

---

### Java Swing 2D Oyun Motoru

Proje hakkında bilgiler, resim

[Java-2D-Game-Engine](/my-projects/java-swing-game-engine)

---

### G4tor - Java Socket Dosya Transferi

Proje hakkında bilgiler, resim

[G4tor](/my-projects/g4tor)

---

### Bilgisayar Terimleri Sözlüğü

Proje hakkında bilgiler, resim

[Bilgisayar Terimleri Sozlugu](/my-projects/bilgisayar-terimleri-sozlugu/)

---

### İşletim Sistemleri Dizin Yapısı

Proje hakkında bilgiler, resim

[Operating Systems Directory Structures](/my-projects/directory-structures/)

---

<footer style="float:left;"><small>&copy; 2022 thealper2</small></footer>
<footer style="float:right;"><small><a href="https://github.com/thealper2">My Github</a></small></footer>