# Loan Underwriting Runbook

These updates are only for AWS re:Invent 2026. Do not merge this branch into the default branch. Contact Ian Douglas or Tomas Josovsky with questions.

[Setup and Walkthrough](#setup-and-walkthrough) | [Booth Setup](#reinvent-2026-booth-setup) | [README](README.md)

## Setup and Walkthrough

Install with `uv sync`. Run `uv run python worker.py` and `uv run python app.py` from the repo root in separate terminals, alongside `temporal server start-dev`. The upstream UI defaults to localhost:8000. AWS credentials/Bedrock model access are required even when Temporal is local. Start an example applicant, review LENNY's recommendation, and send the human decision. Inspect the supervisor and specialist child Workflows. Use synthetic applicants. Stop with Ctrl-C. For Cloud booth mode, use an already deployed Lambda worker and set `LOAN_TASK_QUEUE`; the bundle starts only the web app. See the README for deployment and failure demonstrations. The bundle does not provision Lambda or IAM.

## Sources

[Source README](README.md), [Temporal CLI](https://docs.temporal.io/cli).

## re:Invent 2026 Booth Setup

These updates are only for AWS re:Invent 2026. Do not merge this branch into the default branch. Contact Ian Douglas or Tomas Josovsky with questions.

The laptop bundle uses this demo's source instructions with a separate UI port and a laptop-specific task queue. From the parent `new-demos/` folder, run `./bundle-setup.sh --only loan` and `python3 bundle.py panel`, then start **Loan Underwriting** in [Config](http://127.0.0.1:5199/config). UI: [localhost:5340](http://127.0.0.1:5340/).

Use the shared `.env` from 1Password at the bundle root. Keep machine identity in `.env.local`. The panel keeps local Temporal running in Cloud mode and restarts this demo's owned processes when switching targets. See the [bundle runbook](../RUNBOOK.md) for Cloud prerequisites, offline limits and verification. Runtime is not verified by installation alone.
