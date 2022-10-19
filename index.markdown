---
layout: default
---
<nav>
      <ul style="display: flex;list-style:none">
        {% for item in site.data.menu %}
        <li style="margin-right: 50px"><a style="text-decoration:none" class="{% if page.url == item.link %}active{% endif %}" href="{{ item.link }}">{{ item.title }}</a></li>
        {% endfor %}
      </ul>
</nav>

## About Me

I am a 3rd year computer engineering student.

---

## TryHackMe Badge

<script src="https://tryhackme.com/badge/780082"></script>

---

## A Small Note

This website is still in the coding phase. :)

<strong> Completed: 5 % </strong>

---

<footer style="float:left;"><small>&copy; 2022 thealper2</small></footer>
<footer style="float:right;"><small><a href="https://github.com/thealper2">My Github</a></small></footer>


