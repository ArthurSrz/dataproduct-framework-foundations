# Data product framework

```yaml table
data: data/molecule_reference.csv
width: 300
columns:
  - data: atoms
  - data: __
```

# My Livemark Visualization

```yaml chart
data:
  url: data/molecule_reference.csv
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


# Visualize Data Molecule using a network graph 

```yaml chart
vegalite:
data:
  values: [{'source': 'A', 'target': 'B'},
           {'source': 'B', 'target': 'C'},
           {'source': 'C', 'target': 'D'},
           {'source': 'D', 'target': 'E'},
           {'source': 'E', 'target': 'F'},
           {'source': 'F', 'target': 'A'}]
mark: line
encoding:
  x: {field: "x", type: "quantitative", scale: {zero: false}}
  y: {field: "y", type: "quantitative", scale: {zero: false}}
  detail: {field: "source"}
  detail: {field: "target"}
width: 400
height: 400
autosize: {type: "fit", contains: "padding"}
projections:
  - name: "force"
    type: "force"
    iterations: 300
    forces:
      - force: "charge"
        strength: -50
      - force: "collide"
        radius: 50
      - force: "link"
        distance: 100
        links: "edges"
edges:
  color: "#ccc"
  strokeWidth: 1.5
```