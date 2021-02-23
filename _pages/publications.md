---
layout: archive
title: "Publications"
permalink: /publications/
bg_img: 'https://alpatania.github.io/images/bg_publications.png'
author_profile: true
---



  
{% include base_path %}

  <ul>{% for post in site.publications reversed %}
    {% if post.collection == 'publications'%}
      {% include archive-single-cv.html %}
    {% endif %}
  {% endfor %}</ul>
  
  <p> Pre-prints </p>

  <ul>{% for post in site.pre-print reversed %}
    {% if post.collection == 'pre-prints'%}
      {% include archive-single-cv.html %}
    {% endif %}
  {% endfor %}</ul>

<p style="font-size:15px"> You can also find a full list of my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u></p>
