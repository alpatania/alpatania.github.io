---
layout: archive
title: "Publications"
permalink: /publications/
bg_img: 'https://alpatania.github.io/images/bg_publications.png'
author_profile: true
---



  
{% include base_path %}

  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

  <ul>{% for post in collections.pre-print reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<p> You can also find a list of my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u></p>
