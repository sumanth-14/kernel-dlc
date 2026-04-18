---
name: kernel
description: Agentic delivery runtime. Orchestrates PM, BA, SM, Architect, Developer, QA, Security, and DevOps agents through a 3-phase SDLC (Inception → Construction → Operations) with mandatory deliverables and human approval gates. Activate by starting any request with "Using Kernel, ...".
version: 1.0.0
license: MIT-0
homepage: https://github.com/sumanth-14/kernel-dlc
---

# Kernel — Agentic delivery runtime

## When to use this skill

Activate whenever the user prefixes a request with **"Using Kernel, ..."** — for example:

- `Using Kernel, build a subscription management API`
- `Using Kernel, add OAuth2 login to the existing app`
- `Using Kernel, fix the race condition in the payment queue`

Also activate when the user asks for "full SDLC", "formal delivery process", "with approval gates", or references PRD/BRD/FRS/HLD/LLD artifacts.

## How to load the framework

On activation, load these files **from the user's workspace** (not from this skill directory):

1. **Always first:** `.kernel/common/process-overview.md`
2. **If `.kernel/artifacts/state.md` exists:** `.kernel/common/session-continuity.md`
3. **Before any artifact output:** `.kernel/common/quality-standards.md`
4. **Before any audit log write:** `.kernel/common/audit-format.md`
5. **Per active agent stage:** the matching file under `.kernel/inception/`, `.kernel/construction/`, or `.kernel/operations/`
6. **Root orchestrator rules:** `CLAUDE.md`

## If the framework is not installed in the workspace

If `.kernel/` does not exist in the current workspace, tell the user:

> Kernel framework files are not present in this project. Install them with:
> ```
> npx skills add sumanth-14/kernel-dlc
> ```
> Or clone directly:
> ```
> git clone https://github.com/sumanth-14/kernel-dlc.git .kernel-source
> cp -r .kernel-source/.kernel .kernel-source/CLAUDE.md ./
> ```

Do not attempt to proceed without the rule files loaded.

## Version check

The installed version is declared above (`version: 1.0.0`). Before starting a new project cycle, suggest the user check https://github.com/sumanth-14/kernel-dlc/releases for a newer release. If newer exists, they can update with:

```
npx skills add sumanth-14/kernel-dlc --force
```

Do **not** auto-update mid-project — rule changes between versions can invalidate in-flight artifacts. Update at project boundaries only.

## Core principles (non-negotiable — enforced by `CLAUDE.md`)

1. AI proposes. Humans approve. Never auto-proceed past a gate.
2. Every stage produces a documented artifact saved to `.kernel/artifacts/`.
3. All ambiguities resolved via Q&A before implementation.
4. Audit trail (`.kernel/artifacts/audit.md`) updated after every interaction.
5. Code is never generated before architecture is approved.
6. Tests written alongside code — never after deployment.
7. Security review runs before any deployment, no exceptions.

See `CLAUDE.md` in the installed workspace for the full orchestrator definition.
