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
description: A Unit Chart with Small Multiples
data:
  url: data/molecule_reference.csv
width: 300
mark: rect
transform:
  - calculate: ceil(datum.subid/ 6)
    as: Y
  - calculate: datum.subid - (datum.Y - 1) * 6
    as: X
encoding:
  x:
    field: X
    type: ordinal
    axis: null
  y:
    field: Y
    type: ordinal
    axis: null
  color:
    field: atoms
    type: nominal
  column:
    field: __
    type: nominal
  tooltip:
    field: atoms
    type: nominal
```
