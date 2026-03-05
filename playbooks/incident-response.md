# Playbook: Incident Response for LLM Apps

This playbook covers detection, containment, and recovery when an AI system is actively being abused or has suffered a security incident.

---

## Incident Classification

| Severity | Examples |
|----------|---------|
| **P0 — Critical** | Active data exfiltration, unauthorized tool execution causing real-world harm, credentials leaked |
| **P1 — High** | Confirmed jailbreak in production, cross-user data leak, prompt injection confirmed in retrieval |
| **P2 — Medium** | Suspected policy bypass, anomalous tool call volume, system prompt extraction attempt |
| **P3 — Low** | Single failed injection attempt, benign policy probe detected |

---

## Detection Signals

### Automated Alerts (set these up)
- [ ] Secret pattern detected in model output (regex on API key formats, tokens)
- [ ] Refusal rate drops significantly below baseline
- [ ] Tool call volume spike (>2x normal rate for a session)
- [ ] Retrieval anomalies — user accessing unusual document types
- [ ] Repeated policy probe patterns in a single session
- [ ] Cross-user data query patterns

### Manual Investigation Triggers
- User reports unexpected model behavior
- Support ticket mentioning model revealed something it shouldn't
- Internal audit flags unusual output in log review

---

## Response Steps

### Step 1 — Contain (first 15 minutes)
- [ ] Identify the affected session(s) and user(s)
- [ ] If active: terminate session or rate-limit the user
- [ ] Disable any tools that were misused or could be misused
- [ ] Reduce model permissions to read-only if possible
- [ ] Preserve logs — do not delete or rotate during investigation

### Step 2 — Assess (15 minutes – 2 hours)
- [ ] Pull full conversation logs for affected sessions
- [ ] Identify: What data was accessed? What actions were taken? What was output?
- [ ] Determine the attack vector: direct injection, indirect via RAG, tool abuse, other
- [ ] Assess blast radius: is this one user or potentially many?
- [ ] Determine if real-world actions occurred (emails sent, records deleted, etc.)

### Step 3 — Notify
- [ ] If PII or credentials were exposed: notify security/legal immediately
- [ ] If regulated data (GDPR, HIPAA) was involved: initiate compliance notification process
- [ ] Communicate internally to relevant teams (product, engineering, legal)
- [ ] If user data was exposed to another user: notify affected users

### Step 4 — Eradicate
- [ ] Patch the identified vulnerability:
  - Tighten system prompt / instruction hierarchy
  - Restrict retrieval scope
  - Add input/output classifiers
  - Remove or restrict affected tools
- [ ] Rotate any credentials that may have been exposed
- [ ] Remove poisoned documents from knowledge base (if RAG poisoning)
- [ ] Redeploy with fixes

### Step 5 — Recover
- [ ] Re-enable tools and features with tighter controls
- [ ] Monitor closely for 24–48 hours post-fix
- [ ] Validate fix with targeted test cases that reproduce the original attack

### Step 6 — Learn
- [ ] Write a post-mortem (blameless)
- [ ] Add the attack pattern to your regression test suite
- [ ] Update the red teaming checklist with newly discovered vectors
- [ ] Review whether similar vulnerabilities exist in other parts of the system

---

## Post-Mortem Template

```
## Incident Summary
Date:
Severity:
Duration (detection to containment):

## Timeline
- [time] Detection
- [time] Containment
- [time] Eradication
- [time] Recovery

## Root Cause
(What allowed this to happen?)

## Impact
(What data/actions were affected? How many users?)

## What Went Well
-

## What Went Wrong
-

## Action Items
| Item | Owner | Due |
|------|-------|-----|
|      |       |     |
```

---

## What to Log (Always, Before an Incident)
Good incident response starts with good logging. Ensure these are in place:
- Full conversation history per session (with timestamps)
- Tool calls: name, arguments, user context, result
- Retrieval events: query, docs returned, user ID
- Refusal events: trigger type, input pattern
- Output classifier results
- Session metadata: user ID, IP, timestamps
