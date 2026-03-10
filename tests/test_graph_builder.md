# Test: Graph Builder

## Natürliche Sprache
Der Graph Builder soll aus Entities und Relationen einen Graph erzeugen.

## Maschinenlesbare Struktur
input:
  entities:
    - name: "A"
    - name: "B"
  relations:
    - source: "A"
      target: "B"
      relation: "verwendet"

expected:
  nodes_count: 2
  edges_count: 1
