# RAG Poisoning Simulator (Local)

This lab demonstrates a **defensive** concept: how malicious content in retrieved documents can influence an LLM app if you treat retrieved text as instructions.

It uses a toy "retriever" (a list of documents) and a toy "LLM" simulator. No external APIs.

## Run
```bash
cd labs/rag-poisoning-simulator
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

## What you’ll see
- **UNSAFE** mode: retrieved doc text can override behavior.
- **SAFE** mode: retrieved doc text is treated as untrusted data (delimited + labeled).

## Key lesson
Treat retrieval results like user input:
- **label + delimit**
- never allow retrieved text to become "policy"
- log sources + show citations to the user when possible
