# AI Code Vulnerability Examples (Defensive)

## Risk: SQL Injection
Bad: concatenating user input into SQL strings.
Mitigation: parameterized queries.

## Risk: Hardcoded Secrets
Bad: API keys in source.
Mitigation: env vars + secret manager.

## Risk: Weak Crypto
Bad: outdated algorithms or homebrew crypto.
Mitigation: standard libraries and modern configs.
