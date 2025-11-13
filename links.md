---
layout: page
permalink: /links/
title: links
---

<div id="links">
{% for link in site.data.links.android_apps %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
{% for link in site.data.links.pc %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
{% for link in site.data.links.websites %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
{% for link in site.data.links.guitar_players %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
</div>
