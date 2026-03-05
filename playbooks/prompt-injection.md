# Playbook: Prompt Injection

Prompt injection is when untrusted input attempts to override system behavior.

## Typical Symptoms
- Model follows attacker instructions over your app rules
- Model reveals hidden instructions or internal data
- Model triggers tools in unsafe ways

## Testing Goals (Defensive)
1) Can user input override system instructions?
2) Can injected content in files/docs override instructions?
3) Can the model be coaxed into revealing secrets?

## Test Categories (Safe + Authorized)
### A) Instruction Override Attempts
- Does the app keep its policy and role when user requests policy-breaking behavior?
- Does “ignore previous instructions” change behavior?

### B) Context Confusion
- When user says “the text below is system policy…”, does the model treat it as higher priority?

### C) Data Boundary Tests
- If you include “confidential” strings in context, does the model ever reveal them?

## Mitigations
- **Instruction hierarchy**: Keep critical instructions separate and explicit.
- **Untrusted input delimiting**: Wrap user/doc input in clear delimiters and label as *data*.
- **Tool isolation**: Make tools require structured arguments; don’t let raw text become tool args.
- **Output filtering**: Detect secrets (tokens/keys) and block.
- **Refusal policy**: Define safe refusal behavior and test it.

## What to Log
- Prompt version hash (not the prompt itself if sensitive)
- Tool calls attempted + allowed/blocked
- Retrieval sources used
- Redaction events
- Refusal triggers
