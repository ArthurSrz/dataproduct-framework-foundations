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

```yaml chart
data:
  url: data/cars.csv
mark: circle
selection:
  brush:
    type: interval
encoding:
  x:
    type: quantitative
    field: kmpl
    scale:
     domain: [12,25]
  y:
    type: quantitative
    field: price
    scale:
     domain: [100,900]
  color:
    condition:
      selection: brush
      field: type
      type: nominal
    value: grey
  size:
    type: quantitative
    field: bhp
width: 500
height: 300
```