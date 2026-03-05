# Logging & Monitoring

## Recommended logs (avoid raw sensitive content)
- prompt version hash
- model + temperature
- tool calls: name, args schema validation, allow/deny
- retrieved sources IDs (not full content)
- redaction events
- policy/refusal triggers

## Alerts
- spike in denied tool calls
- repeated probing patterns
- repeated “system prompt” requests
- unusual retrieval source access
