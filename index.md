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

