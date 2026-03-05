![](assets/banner.svg)

# AI Security Testing Playbook

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-blue.svg)](CONTRIBUTING.md)
[![Security Policy](https://img.shields.io/badge/Security-Policy-orange.svg)](SECURITY.md)

A practical, defensive playbook for **testing and securing LLM-powered apps** (chatbots, RAG systems, agentic tools, code assistants) in **authorized environments**.

This repository focuses on:
- **How to test** AI systems for common security failures
- **What to log + measure**
- **How to mitigate** issues with practical patterns
- **Hands-on labs** you can run locally

> ⚠️ Ethics & Scope: This repo is for security testing on systems you own or have explicit permission to test. See **[docs/scope-and-ethics.md](docs/scope-and-ethics.md)**.

---

## Quick links

- **Playbooks** → [playbooks/](playbooks/)
- **Checklists** → [checklists/](checklists/)
- **Mitigation patterns** → [patterns/mitigation-patterns.md](patterns/mitigation-patterns.md)
- **Local lab** → [labs/prompt-injection-toy-app/](labs/prompt-injection-toy-app/)
- **Threat modeling** → [docs/threat-modeling.md](docs/threat-modeling.md)

---

## The Top 10 LLM App Security Risks (practical)

1. **Prompt injection** (direct + indirect via docs)
2. **Tool abuse** (unsafe actions, privilege misuse)
3. **Tool-output injection** (model trusts tool output as instructions)
4. **RAG overexposure** (retrieves sensitive docs / too-broad scope)
5. **RAG poisoning** (malicious documents / source spoofing)
6. **Sensitive data leakage** (system prompts, memory, logs)
7. **Authz gaps** (model can access data the user shouldn’t)
8. **Insecure AI-generated code** (weak crypto, injection, auth flaws)
9. **Unsafe defaults in production** (no rate limits, no monitoring)
10. **Evaluation blind spots** (no regression tests for security failures)

Use the checklists here to systematically test each category.

---

## Reference architecture (where attacks happen)

```text
            Untrusted Inputs
   (user, files, URLs, tool outputs)
                  |
                  v
            +-------------+
            |  LLM APP     |  <-- prompt assembly, policy, routing
            +-------------+
             |     |     |
             |     |     +--> RAG (retrieval + docs)
             |     +--------> Tools (APIs / actions)
             +--------------> Response (user)
```

Key idea: **treat anything untrusted as data**, and strictly control how it reaches prompts and tools.

---

## What’s inside

### Playbooks
- Prompt Injection: [playbooks/prompt-injection.md](playbooks/prompt-injection.md)
- Jailbreaks: [playbooks/jailbreaks.md](playbooks/jailbreaks.md)
- Data Leakage: [playbooks/data-leakage.md](playbooks/data-leakage.md)
- Tool / Agent Security: [playbooks/tool-use-security.md](playbooks/tool-use-security.md)
- RAG Security: [playbooks/rag-security.md](playbooks/rag-security.md)
- Code Generation Security: [playbooks/code-generation-security.md](playbooks/code-generation-security.md)
- Incident Response: [playbooks/incident-response.md](playbooks/incident-response.md)

### Checklists
- AI Red Teaming Checklist: [checklists/ai-red-teaming-checklist.md](checklists/ai-red-teaming-checklist.md)
- LLM App Security Review: [checklists/llm-app-security-review.md](checklists/llm-app-security-review.md)
- Secure Prompting Review: [checklists/secure-prompting-review.md](checklists/secure-prompting-review.md)

### Patterns & Metrics
- Attack Taxonomy: [patterns/attack-taxonomy.md](patterns/attack-taxonomy.md)
- Mitigation Patterns: [patterns/mitigation-patterns.md](patterns/mitigation-patterns.md)
- Eval Metrics: [patterns/eval-metrics.md](patterns/eval-metrics.md)
- Logging & Monitoring: [patterns/logging-and-monitoring.md](patterns/logging-and-monitoring.md)

### Labs (local)
- Prompt Injection Toy App: [labs/prompt-injection-toy-app/README.md](labs/prompt-injection-toy-app/README.md)
- RAG Poisoning Simulator: [labs/rag-poisoning-simulator/README.md](labs/rag-poisoning-simulator/README.md)
- Tool Output Injection Simulator: [labs/tool-output-injection-simulator/README.md](labs/tool-output-injection-simulator/README.md)

---

## Quickstart

1) Read the guardrails:
- [docs/scope-and-ethics.md](docs/scope-and-ethics.md)

2) Run a lab locally:
- [labs/prompt-injection-toy-app/README.md](labs/prompt-injection-toy-app/README.md)

3) Use a checklist during reviews:
- [checklists/llm-app-security-review.md](checklists/llm-app-security-review.md)

---

## Optional: GitHub Pages docs (MkDocs)
This repo includes an **MkDocs** config so you can publish docs via GitHub Pages easily:
- `mkdocs.yml`
- `docs/index.md`

To build locally:
```bash
pip install -r docs-requirements.txt
mkdocs serve
```

---

## Contributing
PRs welcome. Please read:
- [CONTRIBUTING.md](CONTRIBUTING.md)
- [SECURITY.md](SECURITY.md)

---

## License
MIT — see [LICENSE](LICENSE).


## Prompt Injection Attack Examples
See: examples/prompt-injection-attacks.md
