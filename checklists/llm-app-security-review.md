# LLM App Security Review

## Architecture
- [ ] What inputs are untrusted? (users, docs, URLs, tool outputs)
- [ ] Does the system separate instructions from data?
- [ ] Does it enforce access control for retrieval/tools?

## Model + Prompting
- [ ] No secrets embedded in prompts
- [ ] Prompt versioned/hashes tracked
- [ ] Refusal behavior defined and tested

## Tools/Agents
- [ ] Least privilege enforced
- [ ] Structured tool calls with schema validation
- [ ] High-impact actions require confirmation

## RAG
- [ ] Document ingestion sanitization policy exists
- [ ] Retrieval scoped to user permissions
- [ ] Citations or transparency for retrieved sources

## Observability
- [ ] Tool allow/deny logs
- [ ] Redaction and policy triggers
- [ ] Alerts for abnormal usage patterns
