---
layout: page
permalink: /songs/
title: songs
---

<div id="songs">
{% for song in site.data.music %}
    <div>
        <h2>{{ song.artist }} - {{ song.song }}</h2>
        <h4>{{ song.date }}</h4>
        {{ song.embed }}
    </div>
{% endfor %}
</div>
