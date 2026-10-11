# What I check on every AI-generated change

Run before merging. Log what was caught in notes/ (private), with the date.

## Correctness
- Does the code match the spec in SPECS.md, including the failure cases?
- Is the merged state validated, not just the incoming patch?
- Edge values: empty, None, zero, negative, very long, wrong type, dates that do not exist (Feb 30).
- Do counts, totals and "checks run" numbers measure what they claim?
- Does the documentation still match the code?

## Security
- Authorization is checked before any state changes.
- Untrusted input (user text, model output, fetched pages) is validated and fenced before it reaches a tool, a query or a template.
- Secrets come from the environment or a secrets manager, never from code or logs.
- Least privilege: the database role and the tool allowlist only permit what the feature needs.
- Every tool call the agent makes is written to the audit log.
- Dependencies: pip-audit clean, Semgrep clean.

## Tests
- One failing-edge test per validator.
- Model calls in tests use recorded fixtures, never the live API.
- CI is green before Sunday ends.
