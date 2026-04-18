---
name: kernel-revise
description: Send the current artifact back for revision with specific feedback.
---

The user wants to revise the current artifact rather than approve it.

1. Ask the user (one question): "What specifically needs to change in [current artifact]?"
2. Log the revision request in `.kernel/artifacts/audit.md` with outcome: REVISED, including verbatim user feedback.
3. Re-enter the active agent's workflow to address the feedback.
4. Re-present the gate when revision is complete.
