# Test: Extractor

## Natürliche Sprache
Der Extractor soll Entities erkennen, wenn Wörter großgeschrieben sind.

## Maschinenlesbare Struktur
input:
  text: "Python verwendet Module."

expected_contains:
  entity: "Python"
