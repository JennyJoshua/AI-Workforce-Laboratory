# GitHub Owner Setup Checklist

Some repository administration endpoints are not exposed by the connected GitHub tool. The owner must complete the following in GitHub mobile/web UI.

## Labels to create
Create these labels under **Issues → Labels**. Keep exactly one `state:*` label on each active task.

| Label | Suggested colour | Meaning |
|---|---|---|
| `agent:coordinator` | #5319E7 | Coordinator owns the work item |
| `agent:1` | #1D76DB | Research and analysis worker |
| `agent:2` | #0E8A16 | Implementation worker |
| `agent:3` | #FBCA04 | Testing and QA worker |
| `agent:4` | #D93F0B | Security and review worker |
| `state:todo` | #EDEDED | Not started |
| `state:in-progress` | #1D76DB | Active |
| `state:done` | #0E8A16 | Acceptance criteria met |
| `state:blocked` | #B60205 | Cannot proceed |
| `state:needs-human` | #D93F0B | Owner decision required |
| `control:batch` | #5319E7 | Batch-level work |
| `control:approved` | #0E8A16 | Explicit owner approval recorded for the specified action only |
| `control:rejected` | #B60205 | Owner rejected the specified action |
| `control:retry` | #FBCA04 | One bounded retry authorised by policy |
| `control:high-risk` | #B60205 | Requires elevated review |
| `review:chatgpt` | #8250DF | Prepared for independent ChatGPT review |

The connector currently exposes adding labels to an issue but not creating repository labels. Therefore label creation is a manual owner step; no label-write test is claimed.

## Main branch protection
Open **Settings → Rules → Rulesets** (or **Branches → Add branch protection rule**, depending on the current GitHub UI) and target `main`.

Recommended laboratory safeguards:
- Require a pull request before merging.
- Require at least one approval if the setting is available for this repository/plan.
- Require conversation resolution.
- Require status checks only after the project has stable required checks; do not configure nonexistent checks.
- Block force pushes.
- Block branch deletion.
- Do not enable auto-merge.
- Keep administrator bypass disabled if the UI permits and this does not prevent the owner's intended emergency control.

Because this is a solo-owned repository, a one-approval rule may prevent the owner from merging their own PR. Do not weaken protections blindly; choose the safest available rule and retain the explicit owner review gate. No automated agent may merge regardless of GitHub settings.

## Mobile notifications
In GitHub mobile, ensure notifications are enabled for this repository and that issue mentions/participating conversations are delivered. The owner must confirm receipt of the Phase 1 issue notification; the connector cannot inspect phone notification settings.

## Security
- Keep this public lab free of secrets, private data and production data.
- Do not add API keys until a later approved phase.
- Do not enable workflows yet.
