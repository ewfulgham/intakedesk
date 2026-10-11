# IntakeDesk

An intake agent. Messy requests come in as text or a form. The agent extracts structured fields, checks them against existing records, and proposes an action. Nothing is written to the system of record until a person approves it.

Status: scaffold. Started October 2026. Built in public as a learning project in Python; the design comes from systems I have shipped in PHP.

## Planned stack

FastAPI, Pydantic, Postgres with pgvector, LangGraph, the Anthropic API, an evaluation harness that runs in CI from recorded fixtures, tracing, Docker, AWS (ECS Fargate, RDS, Secrets Manager, Bedrock) managed with Terraform.

## Run the checks

```bash
uv sync --group dev
uv run ruff check .
uv run pytest
```

## How this repo is built

- Every feature starts as a short spec in SPECS.md. Code is written to the spec, with AI assistance, and reviewed against it.
- Every validator gets a test that is supposed to fail.
- CHECKLIST.md is what I check on every AI-generated change before it merges.
