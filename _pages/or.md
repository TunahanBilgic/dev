---
layout: page
title: OR Projects
permalink: /or/
description: Operational Research Projects
nav: false
---

{% assign or_posts = site.posts | where_exp: "p", "p.path contains '_posts/or/'" | reverse %}
{% assign gruplar = or_posts | group_by_exp: "p", "p.path | remove_first: '_posts/or/' | split: '/' | first" | sort: "name" %}

{% for grup in gruplar %}
{% case grup.name %}{% when "salbp" %}{% assign baslik = "SALBP" %}{% else %}{% assign baslik = grup.name | capitalize %}{% endcase %}
## {{ baslik }}

{% for post in grup.items -%}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
{% endfor %}