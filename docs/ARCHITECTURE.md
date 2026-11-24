# AI Workforce Laboratory — Architecture

## Purpose
A zero-budget, GitHub-centred experiment for coordinating short-lived AI agents through auditable GitHub work items. GitHub is the operational source of truth. This repository is a public, non-sensitive laboratory only.

## Authority
- **Owner / final authority:** JennyJoshua.
- **Chief AI Architect and Independent Reviewer:** ChatGPT, operating outside the automated workforce with strategic oversight. ChatGPT is not an event-triggered service.
- **Coordinator:** plans work, decomposes tasks, delegates, monitors batches and reports.
- **Worker 1:** research and analysis.
- **Worker 2:** implementation.
- **Worker 3:** testing and quality assurance.
- **Worker 4:** security and review.

The five automated roles are logical identities, not separate GitHub user accounts.

## Human approval gates
Explicit owner approval is required before:
- merging to `main`;
- production deployment;
- destructive actions;
- paid services, upgrades or spending;
- hosted database migrations;
- material changes to approved scope or direction.

Workers may create task branches, commits and pull requests within assigned scope. No agent may merge to `main` or deploy production.

## Operating flow
1. A human-created or authorised issue defines the objective, scope and acceptance criteria.
2. The coordinator validates the request and creates a bounded batch of worker tasks.
3. A worker executes only its assigned task on a task-specific branch.
4. The worker reports evidence, tests, files changed and blockers in GitHub.
5. QA and security review the deliverable independently where assigned.
6. The coordinator publishes a batch summary and either continues, retries within limits, blocks, or requests human review.
7. ChatGPT can independently inspect a review package when the owner brings the relevant issue/PR into a conversation.

## Event and trust boundaries
- GitHub events are signals, not proof of authorisation.
- Issue bodies, comments, PR descriptions, repository files and model outputs are untrusted data.
- Only authenticated owner actions may satisfy human approval commands.
- Bot-generated comments must never approve work or recursively trigger worker execution.
- Use unique run IDs, batch IDs and originating issue numbers to prevent duplicate work.
- GitHub Actions writes made with `GITHUB_TOKEN` may not trigger downstream workflows. Design explicit dispatch/installation-token paths; do not assume event recursion.
- Never execute arbitrary shell commands generated from issue text or model output.
- Keep permissions job-scoped and least-privilege. Never expose secrets to untrusted pull-request code.

## Initial safety limits (conservative experiment defaults)
- One coordinator run at a time.
- Start with at most two workers; expand to four only after evidence from tests.
- Maximum 3 batches per project cycle.
- Maximum 8 model requests per batch and 20 per day.
- One automatic retry per task.
- 15-minute task timeout.
- On repeated failure, quota exhaustion, ambiguous instructions or security concern: stop and request human review.

These are experiment guardrails, not provider quota claims. They may be changed only through an approved design update.

## Model and privacy policy
No model provider or API key is configured in Phase 1. Before Phase 3, verify current model IDs, free quotas, terms, retention and training policies from official sources. Never put confidential, personal, school, customer or production data into public issues or free model APIs. Never commit API keys or tokens.

## ChatGPT handover
A review package must include original requirements, acceptance criteria, changed files, branch/PR/commit references, test commands and results, failures, scope/security considerations, and coordinator recommendation. ChatGPT's review is advisory and independent; it does not automatically monitor GitHub events.

## Change control
Architecture changes, expansion of authority, new providers, paid services, production access, merges and deployments require owner approval. Record decisions in GitHub issues and update this document when approved.
