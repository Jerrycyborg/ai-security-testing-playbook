# Prompt Injection Toy App (Local)

This lab simulates an LLM app that:
- has a "system policy"
- receives user input
- optionally combines them unsafely

It shows why naive concatenation is risky and demonstrates safer input delimiting.

## Run
```bash
cd labs/prompt-injection-toy-app
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

## What to do
Try entering:
- Normal requests (summaries)
- “Ignore instructions…” style text
Compare UNSAFE vs SAFE mode outputs.

This is a simulation meant for learning patterns, not exploiting real systems.
