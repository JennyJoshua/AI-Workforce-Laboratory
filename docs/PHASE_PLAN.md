# Implementation Phases

## Phase 0 — Integration verification
- [x] Verify connected GitHub account and repository metadata access.
- [x] Verify README file retrieval.
- [ ] Verify safe write operations and issue/PR retrieval.
- [ ] Confirm mobile notification and ChatGPT review handover.

## Phase 1 — GitHub foundation (current)
- [x] Create public throwaway repository.
- [x] Confirm connected account has repository admin/push access.
- [ ] Publish architecture and operating templates.
- [ ] Establish labels and task state conventions.
- [ ] Establish issue/PR templates.
- [ ] Review branch protection/ruleset options and configure a safe main-branch gate.
- [ ] Create Phase 1 integration-test issue and verify phone notification.

## Phase 2 — Event automation without AI
Build and test GitHub Actions event routing, run IDs, idempotency, state transitions and recovery. No model calls.

## Phase 3 — First AI worker (read-only)
After current official provider/quota/privacy verification and explicit owner approval: one worker produces structured findings only. No repository writes by the model.

## Phase 4 — Controlled implementation worker
Task branch, bounded edits, tests and PR creation. No merge or deployment authority.

## Phase 5 — Coordinator and batches
Coordinator consumes worker results, creates bounded batches and produces evidence-based summaries.

## Phase 6 — Human approval gate
Validate owner identity and exact target batch; pause dependent work until an explicit decision.

## Phase 7 — Four-worker integration
Test concurrency, provider failures, quotas, duplicate events, recovery and notification behaviour before considering broader use.

## Release rule
No phase advances merely because a workflow ran. Advance only after documented acceptance tests pass and the owner approves the next gated phase.
