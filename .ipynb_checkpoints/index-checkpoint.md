# Hello

```yaml table
data: data/molecule_reference.csv
width: 300
columns:
  - data: atoms
  - data: __
```

# My Livemark Visualization

<div id="chart"></div>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
d3.json("data.json").then(function(data) {
  var nodes = data.nodes;
  var links = data.links;

  var width = 600;
  var height = 400;

  var svg = d3.select("#chart").append("svg")
    .attr("width", width)
    .attr("height", height);

  var simulation = d3.forceSimulation(nodes)
    .force("link", d3.forceLink(links).id(function(d) { return d.id; }))
    .force("charge", d3.forceManyBody())
    .force("center", d3.forceCenter(width / 2, height / 2));

  var link = svg.selectAll("line")
    .data(links)
    .enter().append("line")
    .attr("stroke", "#999")
    .attr("stroke-width", "2");

  var node = svg.selectAll("circle")
    .data(nodes)
    .enter().append("circle")
    .attr("r", 10)
    .attr("fill", "#333");

  simulation.on("tick", function() {
    link.attr("x1", function(d) { return d.source.x; })
      .attr("y1", function(d) { return d.source.y; })
      .attr("x2", function(d) { return d.target.x; })
      .attr("y2", function(d) { return d.target.y; });

    node.attr("cx", function(d) { return d.x; })
      .attr("cy", function(d) { return d.y; });
  });
});
</script>
