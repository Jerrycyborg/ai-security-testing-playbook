# Changelog

All notable changes to this project will be documented here.

## [Unreleased]
### Planned
- Real LLM API integration for labs (optional API key mode)
- STRIDE threat model table for LLM apps
- Additional attack examples: multi-agent injection, memory poisoning
- Severity ratings (Critical/High/Medium) across all playbooks
- Automated markdown link validation in CI

---

## [0.2.0] - 2026-03-05
### Added
- CHANGELOG.md
- Examples section in MkDocs nav (all 4 example files now visible in docs)
- Examples section properly linked in README

### Fixed
- CI step ordering: `setup-python` now runs before `python -m compileall`
- `.gitignore` now catches `.DS_Store` in all subdirectories (`**/.DS_Store`)
- MkDocs nav now includes RAG Poisoning and Tool Output Injection labs
- README orphaned "Prompt Injection Attack Examples" section replaced with proper Examples list

---

## [0.1.0] - 2026-03-05
### Added
- Initial repository: playbooks, checklists, patterns, labs, docs
- 7 playbooks: Prompt Injection, Jailbreaks, Data Leakage, Tool Use Security, RAG Security, Code Generation Security, Incident Response
- 3 checklists: AI Red Teaming, LLM App Security Review, Secure Prompting Review
- 4 patterns: Attack Taxonomy, Mitigation Patterns, Eval Metrics, Logging & Monitoring
- 3 local labs: Prompt Injection Toy App, RAG Poisoning Simulator, Tool Output Injection Simulator
- MkDocs site with Material theme + GitHub Pages CI/CD workflow
- MIT License, Code of Conduct, Contributing guide, Security policy
