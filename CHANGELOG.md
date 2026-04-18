# Changelog

All notable changes to Kernel are documented here. This project follows [Semantic Versioning](https://semver.org/) — **major** = phase-structure change, **minor** = agent-behavior change, **patch** = fixes.

## [1.0.2] — 2026-04-18

### Fixed
- The `skills` CLI silently filters out dot-prefixed folders during install, so `bundle/.kernel/` in v1.0.1 was dropped and only `CLAUDE.md` made it through. Renamed the bundled rule tree to `bundle/kernel/` (no leading dot) and updated SKILL.md paths. Artifacts in the user's workspace still live at `.kernel/artifacts/` — only the skill's internal bundle path changed.

## [1.0.1] — 2026-04-18

### Fixed
- Skill now self-contains the framework. Previously `npx skills add` installed only the `SKILL.md` stub and expected `CLAUDE.md` + `.kernel/` to already exist in the workspace, leaving new users with an activated-but-unusable skill. The full rule tree is now bundled under `skills/kernel/bundle/` and loaded from there; artifacts still write to `<workspace>/.kernel/artifacts/`.

## [1.0.0] — 2026-04-17

### Added
- Initial public release.
- 3-phase SDLC orchestration: Inception → Construction → Operations.
- 8 specialist agents: Product Manager, Business Analyst, Scrum Master, Architect, Developer, QA Engineer, Security, DevOps.
- Mandatory human approval gates between phases.
- Artifact set: PRD, BRD, FRS, user stories, bolt plan, HLD, LLD, ADRs, API contracts, code review checklist, test report, threat model, security report, runbook, deployment plan.
- Audit log and state tracking under `.kernel/artifacts/`.
- Distribution via skills.sh (`npx skills add sumanth-14/kernel-dlc`) and Claude Code plugin marketplace.
