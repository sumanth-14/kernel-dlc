---
name: kernel
description: Agentic delivery runtime. Orchestrates PM, BA, SM, Architect, Developer, QA, Security, and DevOps agents through a 3-phase SDLC (Inception → Construction → Operations) with mandatory deliverables and human approval gates. Activate by starting any request with "Using Kernel, ...".
version: 1.0.2
license: MIT-0
homepage: https://github.com/sumanth-14/kernel-dlc
---

# Kernel — Agentic delivery runtime

## When to activate

Activate whenever the user prefixes a request with **"Using Kernel, ..."** — for example:

- `Using Kernel, build a subscription management API`
- `Using Kernel, add OAuth2 login to the existing app`
- `Using Kernel, fix the race condition in the payment queue`

Also activate when the user asks for "full SDLC", "formal delivery process", "with approval gates", or references PRD/BRD/FRS/HLD/LLD artifacts.

## How to load the framework

The complete framework is **bundled inside this skill** under the `bundle/` directory. On activation, load these files **from this skill's directory** (not from the user's workspace):

1. **Always first:** `bundle/kernel/common/process-overview.md`
2. **Root orchestrator rules:** `bundle/CLAUDE.md`
3. **If `<workspace>/.kernel/artifacts/state.md` exists** (user has an in-flight cycle): also load `bundle/kernel/common/session-continuity.md`
4. **Before any artifact output:** `bundle/kernel/common/quality-standards.md`
5. **Before any audit log write:** `bundle/kernel/common/audit-format.md`
6. **Per active agent stage:** the matching file under `bundle/kernel/inception/`, `bundle/kernel/construction/`, or `bundle/kernel/operations/`

## Where artifacts go

Generated artifacts (PRD, BRD, FRS, HLD, LLD, ADRs, test reports, security reports, state, audit log) are written to **the user's workspace** at `.kernel/artifacts/`. Create this directory on first activation if it doesn't exist. Never write artifacts back into the skill's `bundle/` directory — that's read-only framework code.

## First-run setup

When activated for the first time in a workspace (no `.kernel/artifacts/` directory yet):

1. Create `.kernel/artifacts/` in the workspace root.
2. Create `.kernel/artifacts/state.md` with the initial state template from `bundle/kernel/common/process-overview.md`.
3. Create empty `.kernel/artifacts/audit.md`.
4. Proceed with the phase-01 workflow.

## Version check

Installed version: `1.0.2`. Before starting a new delivery cycle, optionally check https://github.com/sumanth-14/kernel-dlc/releases for a newer version. Update with:

```
npx skills add sumanth-14/kernel-dlc --force
```

Do **not** auto-update mid-project — rule changes between versions can invalidate in-flight artifacts.

## Core principles (non-negotiable — enforced by `bundle/CLAUDE.md`)

1. AI proposes. Humans approve. Never auto-proceed past a gate.
2. Every stage produces a documented artifact saved to `.kernel/artifacts/`.
3. All ambiguities resolved via Q&A before implementation.
4. Audit trail (`.kernel/artifacts/audit.md`) updated after every interaction.
5. Code is never generated before architecture is approved.
6. Tests written alongside code — never after deployment.
7. Security review runs before any deployment, no exceptions.

See `bundle/CLAUDE.md` for the full orchestrator definition.
