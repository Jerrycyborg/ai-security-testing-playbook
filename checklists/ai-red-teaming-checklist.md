# AI Red Teaming Checklist (Authorized)

## Prompt Injection
- [ ] User instruction override attempts (does app stay on-policy?)
- [ ] Data boundary checks (untrusted text treated as data)
- [ ] Tool call manipulation attempts (agent tools)
- [ ] Tool output injection checks

## Jailbreak Behavior (Defensive)
- [ ] Rephrasing / roleplay / hypothetical framing
- [ ] Obfuscated input patterns (encoding, spacing tricks)

## Data Leakage
- [ ] Secrets leakage (keys/tokens/internal strings)
- [ ] System prompt disclosure attempts
- [ ] Cross-user data leakage checks
- [ ] RAG oversharing checks

## RAG Security
- [ ] Poisoned documents
- [ ] Over-broad retrieval
- [ ] Source trust and access control

## Logging & Monitoring
- [ ] Tool calls logged + reasoned allow/deny
- [ ] Redactions logged
- [ ] Prompt versions tracked (hash)
- [ ] Rate limits / anomaly detection

## Operational
- [ ] Safe defaults in production
- [ ] Incident runbook exists
- [ ] Regression tests for vulnerabilities
