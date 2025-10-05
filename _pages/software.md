---
layout: archive
title: "Software"
permalink: /software/
bg_img: 'https://alpatania.github.io/images/bg_code.png'
author_profile: true
---

{% include base_path %}

{% for post in site.code reversed %}  
  {% if post.collection == 'code' %}  
    {% include archive-single.html %}  
  {% endif %}  
{% endfor %}  
