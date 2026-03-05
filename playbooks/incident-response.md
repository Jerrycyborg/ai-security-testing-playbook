# Playbook: Incident Response for LLM Apps

## Detection signals
- repeated policy probing
- high tool-call volume spikes
- retrieval anomalies (unusual doc access patterns)
- secret redaction triggers

## Response steps
1) Contain: disable risky tools, reduce privileges
2) Assess: identify session and prompts involved
3) Eradicate: patch guardrails, tighten retrieval scope
4) Recover: re-enable tools with controls
5) Learn: add regression tests/evals to prevent recurrence
