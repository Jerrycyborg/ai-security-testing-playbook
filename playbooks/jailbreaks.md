# Playbook: Jailbreaks (Defensive)

Jailbreak testing is checking whether policy restrictions are bypassed.

## What to test
- Does the model comply with disallowed requests after rephrasing?
- Does roleplay/hypothetical framing change compliance?
- Do encoded/obfuscated prompts change compliance?

## Defensive controls
- Strong policy enforcement at the application layer
- Consistent refusal and safe completion patterns
- Monitoring for repeated attempts / “policy probing”
- Rate limits and session-level guardrails
