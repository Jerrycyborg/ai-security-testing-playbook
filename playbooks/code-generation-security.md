# Playbook: AI Code Generation Security

Risks:
- insecure defaults (no auth, weak crypto, unsafe deserialization)
- missing input validation
- SQL injection and command injection
- secrets hardcoded in code

## Testing approach
- Require tests and security checks in CI (SAST, dependency scan)
- Code review prompts that demand threat modeling
- Block merges without lint/tests

## Mitigations
- Secure coding standards + templates
- "Security acceptance criteria" in tickets
- Pre-commit hooks and CI gates
