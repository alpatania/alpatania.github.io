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
  Nonlinear network dynamics are notoriously difficult to understand. Here we study a class of recurrent neural networks called combinatorial threshold-linear networks (CTLNs) whose dynamics are determined by the structure of a directed graph. They are a special case of TLNs, a popular framework for modeling neural activity in computational neuroscience.  
  
  In prior work, CTLNs were found to be surprisingly tractable mathematically. For small networks, the fixed points of the network dynamics can often be completely determined via a series of {\it graph rules} that can be applied directly to the underlying graph.  
  
  For larger networks, it remains a challenge to understand how the global structure of the network interacts with local properties. In this work, we propose a method of covering graphs of CTLNs with a set of smaller {\it directional graphs} that reflect the local flow of activity. While directional graphs may or may not have a feedforward architecture, their fixed point structure is indicative of feedforward dynamics.  
  
  The combinatorial structure of the graph cover is captured by the {\it nerve} of the cover. The nerve is a smaller, simpler graph that is more amenable to graphical analysis. We present three nerve theorems that provide strong constraints on the fixed points of the underlying network from the structure of the nerve. We then illustrate the power of these theorems with some examples.  
  
  Remarkably, we find that the nerve not only constrains the fixed points of CTLNs, but also gives insight into the transient and asymptotic dynamics. This is because the flow of activity in the network tends to follow the edges of the nerve.
</p> 

## What are CTLNs?
<p>Combinatorial threshold-linear networks (CTLNs) are competitive TLNs where the matrix W is determined by a graph G.<br/>
The dynamics is defined on the nodes of the network by the following ordinary differential equation:
</p>


## Fixed points
<p>
  A fixed point is a point in the state space where the rate of change is 0 for all xi.</p>

## The idea of a nerve
<p>
  Directional graphs are graph where we can isolate all the possible subroups of nodes that can support fixed points.<br\>
Knowing which nodes can support fixed points give an intuition of where the dynamics of a network will flow.
We know that if a subgroup of nodes of the network don't allow a fixed point, then the dynamics will never stall in them and will try to always move away from them. </p>

## The Theorems

<style>

div.example {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}

.box {
  font: 10px sans-serif;
}

.box line,
.box rect,
.box circle {
  fill: #111;
  stroke: #000;
  stroke-width: 1.5px;
}

.box .center {
  stroke-dasharray: 3,3;
}

.box .outlier {
  fill: none;
  stroke: #ccc;
}

</style>

<div id="example">
<script src="http://d3js.org/d3.v3.min.js"></script>
<script src="http://bl.ocks.org/mbostock/raw/4061502/0a200ddf998aa75dfdb1ff32e16b680a15e5cb01/box.js"></script>
<script>

var margin = {top: 10, right: 50, bottom: 20, left: 50},
    width = 120 - margin.left - margin.right,
    height = 500 - margin.top - margin.bottom;

var min = Infinity,
    max = -Infinity;

var chart = d3.box()
    .whiskers(iqr(1.5))
    .width(width)
    .height(height);

d3.csv("/morley.csv", function(error, csv) {
  var data = [];

  csv.forEach(function(x) {
    var e = Math.floor(x.Expt - 1),
        r = Math.floor(x.Run - 1),
        s = Math.floor(x.Speed),
        d = data[e];
    if (!d) d = data[e] = [s];
    else d.push(s);
    if (s > max) max = s;
    if (s < min) min = s;
  });

  chart.domain([min, max]);

  var svg = d3.select("div#example").selectAll("svg")
      .data(data)
    .enter().append("svg")
      .attr("class", "box")
      .attr("width", width + margin.left + margin.right)
      .attr("height", height + margin.bottom + margin.top)
    .append("g")
      .attr("transform", "translate(" + margin.left + "," + margin.top + ")")
      .call(chart);

  setInterval(function() {
    svg.datum(randomize).call(chart.duration(1000));
  }, 2000);
});

function randomize(d) {
  if (!d.randomizer) d.randomizer = randomizer(d);
  return d.map(d.randomizer);
}

function randomizer(d) {
  var k = d3.max(d) * .02;
  return function(d) {
    return Math.max(min, Math.min(max, d + k * (Math.random() - .5)));
  };
}

// Returns a function to compute the interquartile range.
function iqr(k) {
  return function(d, i) {
    var q1 = d.quartiles[0],
        q3 = d.quartiles[2],
        iqr = (q3 - q1) * k,
        i = -1,
        j = d.length;
    while (d[++i] < q1 - iqr);
    while (d[--j] > q3 + iqr);
    return [i, j];
  };
}

</script>
</div>
