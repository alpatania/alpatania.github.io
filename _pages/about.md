---
permalink: /
title: "About me"
excerpt: "About me"
author_profile: true
bg_img: 'https://alpatania.github.io/images/bg_about.png'
redirect_from:
  - /about/
  - /about.html
---
<p style = "font-weight: 400;">An algebraic topologist by training, my main focus is to develop and apply new topological approaches to study complex systems. Currently, I apply these techniques to brain and social networks but you can take a look at my full CV <a href="https://alpatania.github.io/cv/"> here</a>!</p>

<p style = "font-weight: 400;">I am currently an Assistant Research Scientist at <a href = "http://iuni.iu.edu/">Indiana University Network Science Institute (IUNI)</a> in Bloomington (IN) and external faculty of the <a href="https://vermontcomplexsystems.org/">Vermont Complex Systems Center</a>. I am a Principal Investigator of an R21 NIH grant on "Integrative Predictive Modeling of Alzheimer's Disease" for which I develop models for the joint analysis of genomics and neuroimaging data. On a daily basis, I work on mathematical modelling for brain networks in close collaboration with Olaf Sporns and his team.</p>

<p style = "font-weight: 400;">I obtained my Ph.D in Applied Mathematics at Politecnico di Torino with a dissertation titled: "Simplicial Data Analysis: theory, practice, and algorithms". During my PhD I worked at I.S.I. Foundation in Torino, where I was a part of the research group on "Mathematics and the foundation of complex systems".  </p>

<!--Here are some of the projects I am focusing on right now:
- Developing new technique for joint analysis of genomics and neuroimaging data for transitional clinical research, joint work with Liana G. Apostolova, MD (part of the IMAGENE project);
- Analysing dMRI lifespan data, joint work with Olaf Sporns, Joshua Faskowitz @ Indiana University
- Developing a stochastic sampler for Directed Simplicial Complexes;
- Studying Mathematical models of community structures in relation to simplicial complexes;
- Topological Data Analysis on Health data (rna transcriptomes, quantitative semantic data, brain networks from fMRI, EEG, DTI).
-->


# News
{% include base_path %}

{% for post in site.posts %}
    {% include archive-single-cv.html %}
  {% endfor %}
