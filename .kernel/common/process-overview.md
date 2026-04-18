# Process Overview — Common Rules
# Load this file at the start of EVERY session before any other rule file.

## SESSION STARTUP CHECKLIST
1. Check if .kernel/artifacts/state.md exists.
   - YES → Offer to resume. Load session-continuity.md.
   - NO  → This is a new project. Begin workspace detection.

## WORKSPACE DETECTION
Scan the project root and determine:
  - GREENFIELD: No existing source code. Begin from PM stage.
  - BROWNFIELD: Existing codebase. Load and analyse before requirements.
    → Produce .kernel/artifacts/inception/reverse-engineering.md first.
    → Document: current tech stack, architecture, pain points, dependencies.

## AGENT HANDOFF PROTOCOL
When transitioning between agents, always:
  1. Summarise what the previous agent produced (artefact name + location).
  2. State which agent is now active.
  3. State what this agent's goal is for this session.
  4. Load that agent's rule detail file before generating any output.

Example handoff:
  "✔ Business Analyst has produced: .kernel/artifacts/inception/frs.md
   ▶ Activating: Scrum Master Agent
   Goal: Convert FRS into a structured Bolt Plan with effort estimates."

## HUMAN APPROVAL GATES
Present gates exactly like this — never skip or abbreviate:

  ┌─────────────────────────────────────────────────────────┐
  │ APPROVAL REQUIRED — [Phase/Stage Name]                  │
  ├─────────────────────────────────────────────────────────┤
  │ Artefacts produced:                                     │
  │   • [artefact 1] → .kernel/artifacts/[path]                   │
  │   • [artefact 2] → .kernel/artifacts/[path]                   │
  ├─────────────────────────────────────────────────────────┤
  │ To proceed type: APPROVE                                │
  │ To revise type:  REVISE [what to change]                │
  │ To abort type:   ABORT                                  │
  └─────────────────────────────────────────────────────────┘

## CLARIFICATION PROTOCOL
- Ask ONE question at a time. Wait for the answer before asking the next.
- Record every Q&A pair verbatim in audit.md.
- If after 3 rounds a requirement is still ambiguous, document the assumption
  made, tag it with [ASSUMPTION], and flag for stakeholder review.
- Never make silent assumptions.

## PROGRESS TRACKING
Update .kernel/artifacts/state.md after every completed stage:

  ## Status: [IN PROGRESS | AWAITING APPROVAL | COMPLETE]
  ## Current Phase: [01 Inception | 02 Construction | 03 Operations]
  ## Current Stage: [Agent name]
  ## Last Updated: [ISO timestamp]
  ## Completed Stages:
    - [x] PM — PRD produced
    - [x] BA — FRS produced
    - [ ] SM — Bolt Plan (in progress)
  ## Pending:
    - Human approval of Bolt Plan
