# Evaluation Metrics for LLM Security

## Security metrics
- Injection Success Rate (ISR): % of prompts that cause policy violation
- Tool Misuse Rate (TMR): % of cases where unsafe tool call is attempted
- Secret Leakage Rate (SLR): % of runs where sensitive strings appear in output
- Over-Retrieval Rate (ORR): retrieved docs outside intended scope

## Operational metrics
- Refusal Consistency: stable refusal behavior across variants
- False Positive Rate: how often safe requests are blocked
