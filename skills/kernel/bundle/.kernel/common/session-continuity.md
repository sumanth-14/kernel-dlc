# Session Continuity Rules
# Load this file when .kernel/artifacts/state.md already exists.

## RESUME PROTOCOL
1. Read .kernel/artifacts/state.md fully before saying anything.
2. Present a session summary to the user:

   "Welcome back. Here is where we left off:
    Phase: [01 Inception / 02 Construction / 03 Operations]
    Stage: [Agent name]
    Last action: [Last entry in audit.md]
    Pending: [What needs to happen next]

    Options:
    A) Continue from [current stage]
    B) Review the last artefact produced
    C) Start a new request (will create a new bolt)"

3. Wait for the user's choice before doing anything.
4. Never assume the user wants to continue — always confirm.

## CONTEXT LOADING ON RESUME
When resuming Construction phase, always re-read:
  - .kernel/artifacts/inception/frs.md          (requirements context)
  - .kernel/artifacts/construction/hld.md       (architecture context)
  - .kernel/artifacts/construction/lld.md       (if exists)
  - Current unit's functional-design doc (if in mid-unit)

This prevents the agent from contradicting earlier decisions.

## BOLT NUMBERING
Each independent piece of work gets a bolt number:
  bolt-01, bolt-02, bolt-03 ...

Bolts are tracked in .kernel/artifacts/state.md under:
  ## Bolts:
    - bolt-01: User Authentication — COMPLETE
    - bolt-02: Payment Integration — IN PROGRESS (Developer stage)
    - bolt-03: Notification System — NOT STARTED
