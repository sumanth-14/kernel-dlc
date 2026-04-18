---
name: kernel-approve
description: Approve the current phase gate and advance to the next stage.
---

The user is approving the current approval gate (per `CLAUDE.md` rules).

1. Read `.kernel/artifacts/state.md` to identify the current stage and pending gate.
2. Read `.kernel/common/audit-format.md` and append a gate-approval entry to `.kernel/artifacts/audit.md` with outcome: APPROVED.
3. Update `.kernel/artifacts/state.md` to mark the stage complete and the next stage as in progress.
4. Load the next agent's rule file from `.kernel/` and execute the handoff protocol.

Never approve on behalf of the user without explicit `/kernel-approve` or "APPROVE" input.
