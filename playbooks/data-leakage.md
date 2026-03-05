# Playbook: Data Leakage

Data leakage includes:
- secrets in system prompts
- sensitive conversation memory
- RAG document leakage (over-sharing)
- tool output leakage (DB results, logs)

## Test checklist
- Secrets appear in outputs? (keys, tokens, internal strings)
- Does the app reveal internal instructions?
- Can user cause retrieval of unrelated sensitive docs?

## Mitigations
- Never place secrets in prompts
- Use scoped retrieval and access control
- Redact tool outputs before feeding back to the model
- Avoid logging raw prompts containing sensitive data
