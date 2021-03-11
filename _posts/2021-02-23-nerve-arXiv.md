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
<p>Combinatorial threshold-linear networks (CTLNs) are competitive TLNs where the matrix W is determined by a graph G.
The dynamics is defined on the nodes of the network by the following ordinary differential equation:
</p>


## Fixed points
<p>
  A fixed point is a point in the state space where the rate of change is 0 for all xi.</p>

## The idea of a nerve
<p>
  Directional graphs are graph where we can isolate all the possible subroups of nodes that can support fixed points.<\br>
Knowing which nodes can support fixed points give an intuition of where the dynamics of a network will flow.
We know that if a subgroup of nodes of the network don't allow a fixed point, then the dynamics will never stall in them and will try to always move away from them. </p>

## The Theorems

<!--
\\ defining a new div class

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

</style>-->

<script src="https://d3js.org/d3.v6.min.js"></script>
<!--<script src="http://bl.ocks.org/mbostock/raw/4061502/0a200ddf998aa75dfdb1ff32e16b680a15e5cb01/box.js"></script>-->

<!--<script>
<div id='example'>
</div>

  var width = 400, height = 400;
  var svg = d3.select('#example')
		.append('svg')
		.attr('width', width)
		.attr('height', height);
  
  var vectorcircle = svg.append('circle')
	.attr('cx', width/2)
	.attr('cy', height/2)
	.attr('r', 100)
	.style('fill', 'orange')
	.style('stroke', 'blue')
	.style('stroke-width', '3px')
  </script>-->

<svg height="200" width="500"></svg>

<!--
<script>
var datapoints = [
  {'name': 'New York', 'x': 110, 'y': 10},
  {'name': 'Texas', 'x': 110, 'y': 20},
  {'name': 'California', 'x': 100, 'y': 30},
  {'name': 'Florida', 'x': 120, 'y': 30,
  {'name': 'Illinois', 'x': 110, 'y': 40}
];

var svg = d3.select('svg');
var rectangles = svg.selectAll('circle')
                    .data(datapoints)
                    .enter()
                    .append('circle')
                    .attr('cx', function(d) { return d['x'] * 3 ; })
                    .attr('cy', function(d) { return d['y'] * 3 ; })
                    .attr('r', 5)
		    .style('fill', 'orange')
		    .style("opacity", 0.5)
		  
var edges = [
  {'source': 0,'target': 1},
  {'source': 1,'target': 2},
  {'source': 2,'target': 3},
  {'source': 3,'target': 4},
  {'source': 4,'target': 0}
];

var rectangles = svg.selectAll('line')
  .data(edges)
  .enter()
  .append("line")
  .style("stroke-width", "1px")
  .style("stroke", "#CC9999")

</script>
-->

<script>

    var w = 1000;
    var h = 600;
    var linkDistance=200;

    var colors = d3.scale.category10();

    var dataset = {

    nodes: [
    {name: "Adam"},
    {name: "Bob"},
    {name: "Carrie"},
    {name: "Donovan"},
    {name: "Edward"},
    {name: "Felicity"},
    {name: "George"},
    {name: "Hannah"},
    {name: "Iris"},
    {name: "Jerry"}
    ],
    edges: [
    {source: 0, target: 1},
    {source: 0, target: 2},
    {source: 0, target: 3},
    {source: 0, target: 4},
    {source: 1, target: 5},
    {source: 2, target: 5},
    {source: 2, target: 5},
    {source: 3, target: 4},
    {source: 5, target: 8},
    {source: 5, target: 9},
    {source: 6, target: 7},
    {source: 7, target: 8},
    {source: 8, target: 9}
    ]
    };

 
    var svg = d3.select("svg").attr({"width":w,"height":h});

    var force = d3.layout.force()
        .nodes(dataset.nodes)
        .links(dataset.edges)
        .size([w,h])
        .linkDistance([linkDistance])
        .charge([-500])
        .theta(0.1)
        .gravity(0.05)
        .start();

 

    var edges = svg.selectAll("line")
      .data(dataset.edges)
      .enter()
      .append("line")
      .attr("id",function(d,i) {return 'edge'+i})
      .attr('marker-end','url(#arrowhead)')
      .style("stroke","#ccc")
      .style("pointer-events", "none");
    
    var nodes = svg.selectAll("circle")
      .data(dataset.nodes)
      .enter()
      .append("circle")
      .attr({"r":15})
      .style("fill",function(d,i){return colors(i);})
      .call(force.drag)


    var nodelabels = svg.selectAll(".nodelabel") 
       .data(dataset.nodes)
       .enter()
       .append("text")
       .attr({"x":function(d){return d.x;},
              "y":function(d){return d.y;},
              "class":"nodelabel",
              "stroke":"black"})
       .text(function(d){return d.name;});

    var edgepaths = svg.selectAll(".edgepath")
        .data(dataset.edges)
        .enter()
        .append('path')
        .attr({'d': function(d) {return 'M '+d.source.x+' '+d.source.y+' L '+ d.target.x +' '+d.target.y},
               'class':'edgepath',
               'fill-opacity':0,
               'stroke-opacity':0,
               'fill':'blue',
               'stroke':'red',
               'id':function(d,i) {return 'edgepath'+i}})
        .style("pointer-events", "none");

    var edgelabels = svg.selectAll(".edgelabel")
        .data(dataset.edges)
        .enter()
        .append('text')
        .style("pointer-events", "none")
        .attr({'class':'edgelabel',
               'id':function(d,i){return 'edgelabel'+i},
               'dx':80,
               'dy':0,
               'font-size':10,
               'fill':'#aaa'});

    edgelabels.append('textPath')
        .attr('xlink:href',function(d,i) {return '#edgepath'+i})
        .style("pointer-events", "none")
        .text(function(d,i){return 'label '+i});


    svg.append('defs').append('marker')
        .attr({'id':'arrowhead',
               'viewBox':'-0 -5 10 10',
               'refX':25,
               'refY':0,
               //'markerUnits':'strokeWidth',
               'orient':'auto',
               'markerWidth':10,
               'markerHeight':10,
               'xoverflow':'visible'})
        .append('svg:path')
            .attr('d', 'M 0,-5 L 10 ,0 L 0,5')
            .attr('fill', '#ccc')
            .attr('stroke','#ccc');
     

    force.on("tick", function(){

        edges.attr({"x1": function(d){return d.source.x;},
                    "y1": function(d){return d.source.y;},
                    "x2": function(d){return d.target.x;},
                    "y2": function(d){return d.target.y;}
        });

        nodes.attr({"cx":function(d){return d.x;},
                    "cy":function(d){return d.y;}
        });

        nodelabels.attr("x", function(d) { return d.x; }) 
                  .attr("y", function(d) { return d.y; });

        edgepaths.attr('d', function(d) { var path='M '+d.source.x+' '+d.source.y+' L '+ d.target.x +' '+d.target.y;
                                           //console.log(d)
                                           return path});       

        edgelabels.attr('transform',function(d,i){
            if (d.target.x<d.source.x){
                bbox = this.getBBox();
                rx = bbox.x+bbox.width/2;
                ry = bbox.y+bbox.height/2;
                return 'rotate(180 '+rx+' '+ry+')';
                }
            else {
                return 'rotate(0)';
                }
        });
    });

</script>
