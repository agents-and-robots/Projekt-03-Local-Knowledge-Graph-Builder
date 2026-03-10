# Local Knowledge Graph Builder (Offline, CPU-only)

Dieses Projekt extrahiert aus lokalen Textdateien einen einfachen Knowledge Graph.
Es arbeitet vollständig offline, benötigt keine GPU und verwendet keine KI-Modelle.

Der Knowledge Graph besteht aus:
- Entities (Begriffe, Konzepte)
- Relations (z. B. "ist Teil von", "verwendet", "besteht aus")
- Edges (Verbindungen zwischen Entities)

Das Projekt demonstriert:
- regelbasierte NLP
- heuristische Extraktion
- agentische Verarbeitung
- deterministische Offline-Analyse
- Prompt-Driven Development (PDD)

## Projektstruktur

/src  
    extractor.py  
    relationer.py  
    graph_builder.py  
    agent.py  

/docs  
    architecture.md  

/tests  
    test_extractor.md  
    test_relationer.md  
    test_graph_builder.md  
    test_agent.md  

hardware-requirements.md  
instructions.md  
README.md  
credits.md

## Hardware Requirements

Dieses Projekt ist vollständig lokal ausführbar und benötigt keine spezielle Hardware.
Siehe `hardware-requirements.md`.

## Lizenz

MIT License.

## Credits

Siehe `credits.md`.
