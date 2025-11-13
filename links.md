---
layout: page
permalink: /links/
title: links
---

<div id="links">
<p>android software i like:</p>
{% for link in site.data.links.android_apps %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
<p>pc software i like:</p>
{% for link in site.data.links.pc %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
<p>websites i like:</p>
{% for link in site.data.links.websites %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
<p>guitar players i like:</p>
{% for link in site.data.links.guitar_players %}
    <li><a href="{{ link.link }}">{{ link.name }}</a></li>
{% endfor %}
</div>
