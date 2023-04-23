# Hello

```yaml table
data: data/molecule_reference.csv
width: 300
columns:
  - data: atoms
  - data: __
```

# My Livemark Visualization

```yaml chart
title: My Livemark Visualization
data:
  url: data/data.json
  format:
    type: json
    property: { nodes: "nodes", links: "links" }
mark: "line"
encoding:
  x: { field: "id", type: "quantitative" }
  y: { field: "name", type: "nominal" }
```