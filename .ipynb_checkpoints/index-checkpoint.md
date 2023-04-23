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

#Try 
```yaml chart
data:
  url: data/miserables.json
  format:
    type: json
    property: links

mark: circle
encoding:
  x: 
    field: x
    type: quantitative
    scale:
      zero: false
  y: 
    field: y
    type: quantitative
    scale:
      zero: false
  size: 
    value: 200
  color:
    value: steelblue

selection:
  highlight:
    type: single

  nodes:
    type: multi
    on: "mouseover"
    nearest: true
    empty: "none"
  clear:
    type: multi
    on: "mouseout"
    nearest: true
    empty: "none"

view:
  stroke: null

layout:
  force:
    iterations: 300
    restart: true
    static: false
    forces:
      center: true
      collide:
        radius: 5
      link:
        distance: 100
        strength: 1
      charge:
        strength: -50
```