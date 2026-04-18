# Audit Format Rules
# Every interaction must be logged. Load before any write to audit.md.

## AUDIT LOG FORMAT (.kernel/artifacts/audit.md)

Each entry follows this exact structure:

  ---
  ## [Stage Name or Interaction Type]
  **Timestamp**: [ISO 8601 — e.g. 2026-04-10T14:32:00Z]
  **Agent**: [Product Manager | Business Analyst | Scrum Master |
              Architect | Developer | QA Engineer | Security | DevOps]
  **User Input**: "[Complete raw user input — NEVER summarised or paraphrased]"
  **AI Action**: "[What the agent did — e.g. 'Produced FRS v1.0']"
  **Artefact**: [Path to artefact, e.g. .kernel/artifacts/inception/frs.md]
  **Decision**: "[Any decision made, assumption recorded, or gate outcome]"
  ---

## CRITICAL AUDIT RULES
1. NEVER summarise or paraphrase user input. Capture it verbatim.
2. Log every interaction — not just approvals.
3. Record every [ASSUMPTION] with the rationale.
4. Record every REVISE cycle with what changed and why.
5. Record gate outcomes: APPROVED / REVISED / ABORTED.
6. Overwrite audit.md completely on each write (read → append → rewrite).
   This prevents file corruption from partial writes.

## ASSUMPTION TAGGING
When a gap exists in requirements, document it:

  [ASSUMPTION] Field: payment_currency
  Assumed: USD (default)
  Reason: Stakeholder did not specify. Will default to USD.
  Impact: If multi-currency is needed, this requires a schema change.
  Review By: Stakeholder at next approval gate.

## VERSION TAGGING ON ARTEFACTS
Every artefact header must include:

  # [Document Name]
  **Version**: 1.0
  **Status**: DRAFT | APPROVED | SUPERSEDED
  **Author**: [Agent name]
  **Reviewed By**: [Human approver name / "Pending"]
  **Date**: [ISO date]
  **Change Log**:
    - v1.0: Initial draft
