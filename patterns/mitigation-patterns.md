# Mitigation Patterns

## Pattern: Delimit and Label Untrusted Input
Wrap user/doc text in delimiters and label as data, not instructions.

## Pattern: Least Privilege Tools
Tools should have minimal permissions, and actions should be allowlisted.

## Pattern: Structured Tool Calls
Use strict schemas (JSON) and validate arguments.

## Pattern: Output Redaction
Detect and redact tokens, keys, and PII before returning.

## Pattern: Retrieval Scope Control
Enforce per-user access control on documents and limit top-k retrieval.

## Pattern: Human-in-the-loop
Require confirmation for irreversible or high-impact actions.
