# Playbook: Tool Use / Agent Security

When the model can call tools, the risk increases.

## What to test (Authorized)
- Can user cause the agent to call tools unexpectedly?
- Can user inject instructions into tool outputs (tool-output injection)?
- Can the agent access data beyond user permissions?

## Mitigations
- **Least privilege** for every tool (read-only by default)
- **Structured tool calls** (JSON schema, strict validation)
- **Tool output as untrusted** (treat tool outputs like user input)
- **Human-in-the-loop** for high-impact actions (payments, deletes, sending emails)
- **Allowlist** of actions and destinations
