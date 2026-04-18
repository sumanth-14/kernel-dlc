---
name: kernel-status
description: Show current Kernel delivery state — active phase, agent, last artifact, pending approvals.
---

Read `.kernel/artifacts/state.md` and present a concise status summary:

- **Phase:** (01 Inception | 02 Construction | 03 Operations)
- **Active stage:** (agent name)
- **Last artifact produced:** (path)
- **Pending:** (next action — usually a human approval gate)
- **Completed stages:** (checklist)

If `.kernel/artifacts/state.md` does not exist, respond: "No active Kernel cycle. Start one with /kernel-start."
