# Test: Relationer

## Natürliche Sprache
Der Relationer soll einfache Relationen erkennen.

## Maschinenlesbare Struktur
input:
  entities:
    - name: "Python"
    - name: "Module"
  text: "Python verwendet Module."

expected_contains:
  relation: "verwendet"
