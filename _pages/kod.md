---
layout: page
title: Kodlama Öğreniyorum
permalink: /kod/
description: kodlamaogreniyorum.com Çalışmalar
nav: false
---

{% assign kod_posts = site.posts | where_exp: "p", "p.path contains '_posts/kod/'" | reverse %}
{% assign gruplar = kod_posts | group_by_exp: "p", "p.path | remove_first: '_posts/kod/' | split: '/' | first" | sort: "name" %}

{% for grup in gruplar %}
{% case grup.name %}{% when "matlab" %}{% assign baslik = "MATLAB" %}{% else %}{% assign baslik = grup.name | capitalize %}{% endcase %}
## {{ baslik }}

{% for post in grup.items -%}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
{% endfor %}