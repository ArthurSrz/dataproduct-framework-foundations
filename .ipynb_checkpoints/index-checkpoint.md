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


# My Interactive Vega Visualization


```python
import json
from livemark.renderers import VegaLiteRenderer
# Define your Vega specification here
vega_spec = {
  "$schema": "https://vega.github.io/schema/vega/v5.json",
  "width": 400,
  "height": 400,
  "padding": 5,
  "signals": [
    {"name": "cx", "update": "width / 2"},
    {"name": "cy", "update": "height / 2"},
    {"name": "nodeRadius", "value": 8},
    {"name": "nodeCharge", "value": -30},
    {"name": "linkDistance", "value": 30},
    {"name": "chargeStrength", "value": 0.1}
  ],
  "data": [
    {
      "name": "nodes",
      "values": [
        {"id": "Alice"},
        {"id": "Bob"},
        {"id": "Carol"},
        {"id": "David"}
      ]
    },
    {
      "name": "links",
      "values": [
        {"source": "Alice", "target": "Bob"},
        {"source": "Bob", "target": "Carol"},
        {"source": "Carol", "target": "David"}
      ]
    }
  ],
  "marks": [
    {
      "type": "line",
      "from": {"data": "links"},
      "encode": {
        "enter": {
          "strokeWidth": {"value": 2},
          "strokeOpacity": {"value": 0.5},
          "x": {"field": "source.x"},
          "y": {"field": "source.y"}
        },
        "update": {
          "x2": {"field": "target.x"},
          "y2": {"field": "target.y"}
        }
      }
    },
    {
      "type": "symbol",
      "from": {"data": "nodes"},
      "encode": {
        "enter": {
          "fillOpacity": {"value": 1},
          "strokeWidth": {"value": 2},
          "size": {"value": 64},
          "fill": {"value": "#000"},
          "stroke": {"value": "#fff"},
          "x": {"field": "x"},
          "y": {"field": "y"}
        }
      },
      "transform": [
        {
          "type": "force",
          "static": False,
          "forces": [
            {"force": "center", "x": {"signal": "cx"}, "y": {"signal": "cy"}},
            {"force": "collide", "radius": {"signal": "nodeRadius"}},
            {"force": "nbody", "strength": {"signal": "nodeCharge"}},
            {"force": "link", "links": "links", "distance": {"signal": "linkDistance"}},
            {"force": "charge", "strength": {"signal": "chargeStrength"}}
          ]
        }
      ]
    }
  ]
}
vl_renderer = VegaLiteRenderer(spec=vega_spec)
vl_renderer.render()
print(vl_renderer.html)
```
