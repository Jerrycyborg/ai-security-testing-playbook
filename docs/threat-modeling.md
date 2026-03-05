# Threat Modeling for LLM Apps

## Step 1 — Map the system
- Inputs: user messages, documents, URLs, files
- Model: provider, version, settings
- Context: system prompt, memory, conversation state
- Tools: APIs/actions the model can invoke
- Outputs: model responses, tool results, logs

## Step 2 — Identify assets
- Secrets: API keys, tokens, credentials
- Sensitive data: customer PII, internal documents
- Tool permissions: ability to read/write/execute
- Integrity: whether the model can cause actions or code changes

## Step 3 — Identify threats
Common categories:
- Prompt injection
- Data leakage (logs, context, tool outputs)
- Unsafe tool use (privilege escalation via tool calls)
- RAG poisoning (malicious docs)
- Supply-chain risks (plugins, agent tools)
- Insecure generated code

## Step 4 — Controls
- Isolation: separate untrusted inputs from system instructions
- Least privilege tools
- Output validation and policy checks
- Retrieval filtering and source trust
- Logging + anomaly detection
