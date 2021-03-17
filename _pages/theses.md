---
layout: archive
title: "Theses"
permalink: /theses/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my theses on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.theses reversed %}
  {% include archive-single.html %}
{% endfor %}
