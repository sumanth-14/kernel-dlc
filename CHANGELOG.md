# Changelog

All notable changes to Kernel are documented here. This project follows [Semantic Versioning](https://semver.org/) — **major** = phase-structure change, **minor** = agent-behavior change, **patch** = fixes.

## [1.0.0] — 2026-04-17

### Added
- Initial public release.
- 3-phase SDLC orchestration: Inception → Construction → Operations.
- 8 specialist agents: Product Manager, Business Analyst, Scrum Master, Architect, Developer, QA Engineer, Security, DevOps.
- Mandatory human approval gates between phases.
- Artifact set: PRD, BRD, FRS, user stories, bolt plan, HLD, LLD, ADRs, API contracts, code review checklist, test report, threat model, security report, runbook, deployment plan.
- Audit log and state tracking under `.kernel/artifacts/`.
- Distribution via skills.sh (`npx skills add sumanth-14/kernel-dlc`) and Claude Code plugin marketplace.
