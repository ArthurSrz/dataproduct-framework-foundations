# Hello

```yaml table
data: data/molecule_reference.csv
width: 300
columns:
  - data: atoms
  - data: __
```

```yaml chart
$schema: https://vega.github.io/schema/vega/v5.json
data:
  - name: nodes
    values:
      - {id: "A", group: "1"}
      - {id: "B", group: "2"}
      - {id: "C", group: "1"}
  - name: links
    values:
      - {source: "A", target: "B"}
      - {source: "B", target: "C"}    
scales:
  - name: color
    type: ordinal
    range: category10
    domain: {data: "nodes", field: "group"}
marks:
  - type: line
    from: {data: "links"}
    encode:
      enter:
        stroke: {value: "grey"}
      update:
        x: {scale: "x", field: "source"}
        y: {scale: "y", field: "target"}
  - type: symbol
    from: {data: "nodes"}
    encode:
      enter:
        fill: {scale: "color", field: "group"}
        stroke: {value: "white"}
        size: {value: 200}
      update:
        x: {scale: "x", field: "id"}
        y: {scale: "y", value: 100}
```