# Playbook: RAG Security (Retrieval-Augmented Generation)

RAG risks:
- Poisoned documents with hidden instructions
- Over-broad retrieval exposes sensitive data
- Source spoofing / low-trust content

## Tests
- Injected instructions inside documents: does the model follow them?
- Retrieval scope: can you query docs you shouldn't see?
- Prompt/data separation: does the app label retrieved text as data?

## Mitigations
- Access control and per-user retrieval scope
- Document trust scoring / allowlisted sources
- Strip or neutralize instruction-like content during ingestion (carefully)
- Cite sources and show what was retrieved to the user (transparency)
