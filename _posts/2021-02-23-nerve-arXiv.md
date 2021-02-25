---
title: 'New pre-print: Nerve theorems for fixed points of neural networks'
date: 2021-02-23
permalink: /posts/2021/02/nerve-arXiv/
tags:
  - CTLNs
  - 'Women In Computational Topology'
  - pre-print
---

<a href="https://arxiv.org/abs/2102.11437"> Nerve theorems for fixed points of neural networks</a>  

<p>
  Nonlinear network dynamics are notoriously difficult to understand. Here we study a class of recurrent neural networks called combinatorial threshold-linear networks (CTLNs) whose dynamics are determined by the structure of a directed graph. They are a special case of TLNs, a popular framework for modeling neural activity in computational neuroscience. In prior work, CTLNs were found to be surprisingly tractable mathematically. For small networks, the fixed points of the network dynamics can often be completely determined via a series of {\it graph rules} that can be applied directly to the underlying graph. For larger networks, it remains a challenge to understand how the global structure of the network interacts with local properties. In this work, we propose a method of covering graphs of CTLNs with a set of smaller {\it directional graphs} that reflect the local flow of activity. While directional graphs may or may not have a feedforward architecture, their fixed point structure is indicative of feedforward dynamics. The combinatorial structure of the graph cover is captured by the {\it nerve} of the cover. The nerve is a smaller, simpler graph that is more amenable to graphical analysis. We present three nerve theorems that provide strong constraints on the fixed points of the underlying network from the structure of the nerve. We then illustrate the power of these theorems with some examples. Remarkably, we find that the nerve not only constrains the fixed points of CTLNs, but also gives insight into the transient and asymptotic dynamics. This is because the flow of activity in the network tends to follow the edges of the nerve.
</p> 

## What are CTLNs?

<form>
  <input type="number" name="delta" id="delta" min="0" value="2" > 
  <input type="number" name="epsilon" id="epsilon" min="0" max="0.66" >
  <input type="submit" value="Refresh" > 
</form>

## Fixed points

## The idea of a nerve

## The Theorems

<style>


path {
  fill-rule: evenodd;
  stroke: #333;
  stroke-width: 2px;
}

.sun path {
  fill: #6baed6;
}

.planet path {
  fill: #9ecae1;
}

.annulus path {
  fill: #c6dbef;
}

</style>
<form>
  <input type="radio" name="reference" id="ref-annulus">
  <label for="ref-annulus">Annulus</label><br>
  <input type="radio" name="reference" id="ref-planet" checked>
  <label for="ref-planet">Planets</label><br>
  <input type="radio" name="reference" id="ref-sun">
  <label for="ref-sun">Sun</label>
</form>

<script>

var width = 960,
    height = 500,
    radius = 80,
    x = Math.sin(2 * Math.PI / 3),
    y = Math.cos(2 * Math.PI / 3);

var offset = 0,
    speed = 4,
    start = Date.now();

var svg = d3.select("body").append("svg")
    .attr("width", width)
    .attr("height", height)
  .append("g")
    .attr("transform", "translate(" + width / 2 + "," + height / 2 + ")scale(.55)")
  .append("g");

var frame = svg.append("g")
    .datum({radius: Infinity});

frame.append("g")
    .attr("class", "annulus")
    .datum({teeth: 80, radius: -radius * 5, annulus: true})
  .append("path")
    .attr("d", gear);

frame.append("g")
    .attr("class", "sun")
    .datum({teeth: 16, radius: radius})
  .append("path")
    .attr("d", gear);

frame.append("g")
    .attr("class", "planet")
    .attr("transform", "translate(0,-" + radius * 3 + ")")
    .datum({teeth: 32, radius: -radius * 2})
  .append("path")
    .attr("d", gear);

frame.append("g")
    .attr("class", "planet")
    .attr("transform", "translate(" + -radius * 3 * x + "," + -radius * 3 * y + ")")
    .datum({teeth: 32, radius: -radius * 2})
  .append("path")
    .attr("d", gear);

frame.append("g")
    .attr("class", "planet")
    .attr("transform", "translate(" + radius * 3 * x + "," + -radius * 3 * y + ")")
    .datum({teeth: 32, radius: -radius * 2})
  .append("path")
    .attr("d", gear);

d3.selectAll("input[name=reference]")
  .data([radius * 5, Infinity, -radius])
    .on("change", function(radius1) {
      var radius0 = frame.datum().radius, angle = (Date.now() - start) * speed;
      frame.datum({radius: radius1});
      svg.attr("transform", "rotate(" + (offset += angle / radius0 - angle / radius1) + ")");
    });

d3.selectAll("input[name=speed]")
    .on("change", function() { speed = +this.value; });

function gear(d) {
  var n = d.teeth,
      r2 = Math.abs(d.radius),
      r0 = r2 - 8,
      r1 = r2 + 8,
      r3 = d.annulus ? (r3 = r0, r0 = r1, r1 = r3, r2 + 20) : 20,
      da = Math.PI / n,
      a0 = -Math.PI / 2 + (d.annulus ? Math.PI / n : 0),
      i = -1,
      path = ["M", r0 * Math.cos(a0), ",", r0 * Math.sin(a0)];
  while (++i < n) path.push(
      "A", r0, ",", r0, " 0 0,1 ", r0 * Math.cos(a0 += da), ",", r0 * Math.sin(a0),
      "L", r2 * Math.cos(a0), ",", r2 * Math.sin(a0),
      "L", r1 * Math.cos(a0 += da / 3), ",", r1 * Math.sin(a0),
      "A", r1, ",", r1, " 0 0,1 ", r1 * Math.cos(a0 += da / 3), ",", r1 * Math.sin(a0),
      "L", r2 * Math.cos(a0 += da / 3), ",", r2 * Math.sin(a0),
      "L", r0 * Math.cos(a0), ",", r0 * Math.sin(a0));
  path.push("M0,", -r3, "A", r3, ",", r3, " 0 0,0 0,", r3, "A", r3, ",", r3, " 0 0,0 0,", -r3, "Z");
  return path.join("");
}

d3.timer(function() {
  var angle = (Date.now() - start) * speed,
      transform = function(d) { return "rotate(" + angle / d.radius + ")"; };
  frame.selectAll("path").attr("transform", transform);
  frame.attr("transform", transform); // frame of reference
});

</script>

<body>
</body>
