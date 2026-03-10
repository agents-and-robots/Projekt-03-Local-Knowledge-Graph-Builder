# LLM Instructions – Local Knowledge Graph Builder (Offline)

Diese Datei definiert alles, was ein LLM benötigt, um dieses Projekt vollständig selbständig umzusetzen:
- Input/Output-Protokoll
- Agenten-Logik
- Regelwerk
- Aufgabenbeschreibung
- Hardware-Constraints
- How-To-Use

---

## 1. Ziel

Erstelle ein System, das lokale Textdateien analysiert, Entities extrahiert, Relationen erkennt und daraus einen Knowledge Graph erzeugt — vollständig offline.

---

## 2. Hardware Constraints

Dieses Projekt muss vollständig auf normaler Consumer-Hardware lauffähig sein:

- CPU-only
- keine GPU-Abhängigkeiten
- keine Modelle > 1 GB
- keine externen APIs oder Cloud-Dienste
- alles offline
- Python-Standardbibliothek

---

## 3. Modul-Spezifikationen

### 3.1 Extractor (/src/extractor.py)

Signatur: extract(text: str) -> list[dict]

Aufgabe:
- Entities extrahieren (heuristisch)
- mögliche Patterns:
  - Großgeschriebene Wörter
  - Substantive
  - einfache Regex-Regeln

Rückgabeformat:
- entities: Liste von Objekten:
  - name: string
  - position: int

---

### 3.2 Relationer (/src/relationer.py)

Signatur: relate(entities: list[dict], text: str) -> list[dict]

Aufgabe:
- einfache Relationen erkennen
- heuristische Regeln:
  - „X besteht aus Y“
  - „X verwendet Y“
  - „X ist Teil von Y“

Rückgabeformat:
- relations: Liste von Objekten:
  - source: string
  - target: string
  - relation: string

---

### 3.3 Graph Builder (/src/graph_builder.py)

Signatur: build(entities: list[dict], relations: list[dict]) -> dict

Aufgabe:
- Knowledge Graph als JSON erzeugen

Rückgabeformat:
- graph:
  - nodes: list
  - edges: list

---

### 3.4 Agent (/src/agent.py)

Signatur: run(text: str) -> dict

Aufgabe:
- orchestriert extractor, relationer, graph_builder
- Feedback-Loop (max. 2 Iterationen)

Rückgabeformat:
- graph: dict
- steps: list[str]

---

## 4. Orchestrator-Logik

1. entities = extract(text)
2. relations = relate(entities, text)
3. graph = build(entities, relations)
4. Wenn graph leer oder unbrauchbar:
   - neue Heuristik anwenden
   - zurück zu Schritt 1
5. Ergebnis zurückgeben

---

## 5. Regelwerk / Constraints

### Extraktion
- deterministisch
- keine KI
- keine Modelle
- einfache Regex oder heuristische Regeln

### Relationen
- nur definierte Relationstypen
- keine freien Texte

### Graph
- JSON-Struktur
- deterministisch

### Feedback-Loop
- max. 2 Iterationen

---

## 6. Aufgaben an das LLM

Das LLM soll:

1. extractor.py implementieren  
2. relationer.py implementieren  
3. graph_builder.py implementieren  
4. agent.py implementieren  
5. architecture.md ergänzen  
6. Tests in /tests aktualisieren  

---

## 7. How-To-Use (für Code-Assistenten)

1. Öffne das Repository.  
2. Öffne `instructions.md`.  
3. Markiere den gesamten Inhalt.  
4. Sende ihn an deinen Code-Assistenten mit:

„Lies diese instructions.md vollständig. Implementiere dann alle beschriebenen Module und Dateien. Halte dich strikt an das Input/Output-Protokoll, das Regelwerk und die Hardware-Constraints. Beginne mit extractor.py.“

Damit kann ein LLM das Projekt vollständig autonom umsetzen.
