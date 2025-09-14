# RAG mit ChromaDB

**Autor:** Soufiane El Machkouri

Ein vollständiges **Retrieval-Augmented Generation (RAG)** System mit ChromaDB, LangChain und OpenAI.

## Was ist das?

Dieses Projekt demonstriert, wie man eine RAG-Pipeline aufbaut:
- **Dokumente laden** und in Chunks aufteilen
- **Vektordatenbank** mit ChromaDB erstellen  
- **Ähnlichkeitssuche** für relevante Inhalte
- **LLM-Integration** für intelligente Antworten

## Setup

### 1. uv Package Manager installieren
```bash
pip install uv
```

### 2. Projekt initialisieren
```bash
uv init
uv add -r requirements.txt
```

### 3. OpenAI API Key setzen
Erstelle eine `.env` Datei:
```
OPENAI_API_KEY=dein_api_key_hier
```

### 4. Notebook starten
```bash
jupyter lab chromadb.ipynb
```

## Projektstruktur

```
├── chromadb.ipynb          # Haupt-Notebook mit RAG-Pipeline
├── data/                   # Beispieldokumente über RAG
│   ├── rag_intro.txt
│   ├── rag_architecture.txt
│   └── ...
├── chroma_db/              # Persistente Vektordatenbank
├── pyproject.toml          # uv Dependencies
├── requirements.txt        # Alternative Dependencies
└── README.md              # Diese Datei
```

## Funktionen

### Dokumentverarbeitung
- Lädt Textdateien aus dem `data/` Ordner
- Teilt lange Texte in überlappende Chunks auf
- Erstellt Metadaten für jedes Dokument

### Vektorsuche
- Konvertiert Text zu Embeddings mit OpenAI
- Speichert Vektoren persistent in ChromaDB
- Unterstützt Ähnlichkeitssuche mit Bewertungen

### RAG-Pipeline
- Retriever: Findet relevante Dokumente
- Generator: GPT-3.5-turbo für Antworten
- Prompt Engineering für deutsche Antworten

## Schritte im Notebook

1. **Dependencies laden** - Alle nötigen Bibliotheken importieren
2. **Beispieldaten erstellen** - 6 Textdateien über RAG-Konzepte  
3. **Dokumente laden** - DirectoryLoader für alle .txt Dateien
4. **Text aufteilen** - RecursiveCharacterTextSplitter (500 Zeichen, 50 Überlappung)
5. **Embeddings erstellen** - OpenAI-Embeddings für alle Chunks
6. **Vektordatenbank** - ChromaDB mit persistenter Speicherung
7. **Suche testen** - Similarity Search mit verschiedenen Queries
8. **LLM konfigurieren** - ChatOpenAI mit GPT-3.5-turbo
9. **RAG-Kette** - Retriever + Prompt + LLM kombinieren
10. **Live-Test** - Fragen stellen und Antworten erhalten

## Beispiel-Query

```python
response = rag_chain.invoke({
    "input": "Wie kann ich RAG für einen Chatbot verwenden?"
})
print(response['answer'])
```

## Technologien

- **uv**: Schneller Python Package Manager (anstatt pip)
- **ChromaDB**: Vektordatenbank für Embeddings
- **LangChain**: RAG-Pipeline Framework
- **OpenAI**: Embeddings und GPT-3.5-turbo
- **Python**: Hauptprogrammiersprache


