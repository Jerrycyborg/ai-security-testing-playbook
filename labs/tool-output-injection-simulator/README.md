# Tool Output Injection Simulator (Local)

This lab demonstrates a defensive concept: **tool outputs are untrusted**.
If your app blindly feeds tool output back into the model, a malicious tool response can act like prompt injection.

No external APIs. The "tool" is a toy function that returns a string.

## Run
```bash
cd labs/tool-output-injection-simulator
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

## What you’ll see
- **UNSAFE** mode: model obeys instruction-like tool output.
- **SAFE** mode: tool output is wrapped as data + validated.

## Key mitigations
- Schema-validate tool outputs
- Treat tool output as untrusted data (label + delimit)
- Allowlist tool actions and destinations
