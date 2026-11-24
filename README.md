# AI Workforce Laboratory

A zero-budget, GitHub-centred experiment for a controlled AI agent workforce. This is a public test laboratory only: do not add secrets, confidential information, personal data or production credentials.

## Current status
**Phase 1 — GitHub foundation.** No AI model API, autonomous workflow, repository secret or production integration is enabled.

## Start here
- [Architecture and authority model](docs/ARCHITECTURE.md)
- [Implementation phases and acceptance gates](docs/PHASE_PLAN.md)
- [GitHub owner setup: labels, branch safeguards and notifications](docs/GITHUB_OWNER_SETUP.md)

## Issue and pull request templates
- Agent task: `.github/ISSUE_TEMPLATE/agent-task.md`
- Human review: `.github/ISSUE_TEMPLATE/human-review.md`
- Batch summary: `.github/ISSUE_TEMPLATE/batch-summary.md`
- Pull request: `.github/PULL_REQUEST_TEMPLATE.md`

## Non-negotiable controls
- The repository owner retains final authority.
- No automated merge to `main` or production deployment.
- Human approval is required for destructive actions, paid services, hosted database migrations and material scope changes.
- Treat issues, comments, repository content and model outputs as untrusted input.
- Do not commit API keys or tokens.

See [Phase 1 tracking issue](https://github.com/JennyJoshua/AI-Workforce-Laboratory/issues/1) for current work and evidence.
