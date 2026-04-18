---
name: kernel-start
description: Begin a new Kernel-orchestrated delivery cycle. Loads the framework and prompts for the request.
---

Activate the Kernel agentic delivery runtime.

1. Load `CLAUDE.md` and `.kernel/common/process-overview.md` from the current workspace.
2. If `.kernel/artifacts/state.md` exists, also load `.kernel/common/session-continuity.md` and resume.
3. Prompt the user: "What are we building? Please phrase as: Using Kernel, [your goal]."
4. Follow the standard orchestrator workflow from `CLAUDE.md` — do NOT skip phases or approval gates.

If `.kernel/` is not present in the workspace, instruct the user to run:
`npx skills add sumanth-14/kernel-dlc`
