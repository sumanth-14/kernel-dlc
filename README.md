# Kernel — Agentic delivery runtime

[![License: MIT-0](https://img.shields.io/badge/License-MIT--0-yellow.svg)](https://opensource.org/licenses/MIT-0)
![Version](https://img.shields.io/badge/Version-1.0.0-blue)

An agentic delivery runtime that orchestrates AI agents to ship production-grade software through a full Software Development Life Cycle (SDLC).

## Overview

Kernel coordinates specialized AI agents across all phases of software development—from inception through construction to operations. It enforces quality gates, mandatory deliverables, and formal approval workflows to ensure every delivery meets professional standards.

## Key Features

- **Multi-Agent Orchestration**: Coordinates Product Manager, Business Analyst, Scrum Master, Architect, Developer, QA Engineer, Security, and DevOps agents
- **Phase-Based Workflow**: Structured SDLC phases with mandatory deliverables and human approval gates
- **Adaptive Execution**: Customized workflows for different request types (features, bugs, enhancements, infrastructure changes)
- **Quality Assurance**: Built-in quality standards, security reviews, and audit trails
- **Documentation-First**: Every phase produces documented artifacts for transparency and continuity

## Project Structure

```
kernel/
├── CLAUDE.md                           # Core framework definition
├── .kernel/                            # Agent rules + generated artifacts
│   ├── common/                         # Shared processes and standards
│   │   ├── process-overview.md
│   │   ├── session-continuity.md
│   │   ├── audit-format.md
│   │   └── quality-standards.md
│   ├── inception/                      # Requirements and planning phase
│   │   ├── product-manager.md
│   │   ├── business-analyst.md
│   │   └── scrum-master.md
│   ├── construction/                   # Design and development phase
│   │   ├── architect.md
│   │   ├── developer.md
│   │   └── qa-engineer.md
│   ├── operations/                     # Deployment and security phase
│   │   ├── security.md
│   │   └── devops.md
│   └── artifacts/                      # Generated deliverables (created during execution)
│       ├── state.md                    # Progress tracker
│       ├── audit.md                    # Audit log
│       ├── inception/                  # Phase 1 deliverables
│       ├── construction/               # Phase 2 deliverables
│       └── operations/                 # Phase 3 deliverables
└── README.md                           # This file
```

## SDLC Phases

### Phase 01: Inception
**Agents**: Product Manager → Business Analyst → Scrum Master  
**Deliverables**: PRD, BRD, FRS, User Stories, Sprint/Bolt Plan  
**Gate**: Human approval required before proceeding

### Phase 02: Construction
**Agents**: Architect → Developer → QA Engineer  
**Deliverables**: HLD, LLD, ADRs, Code, Test Suite  
**Gate**: QA sign-off required before proceeding

### Phase 03: Operations
**Agents**: Security Agent → DevOps Agent  
**Deliverables**: Security Review, Deployment Plan, Monitoring Setup  
**Gate**: Security clearance required before deployment

## Workflow Execution

Start every session by stating your intent with "Using Kernel, ...":

```
Using Kernel, build a subscription management API
Using Kernel, add OAuth2 login to the existing app
Using Kernel, fix the race condition in the payment queue
```

The framework will automatically:
1. Load relevant rule files for your request type
2. Execute appropriate phases with the correct agents
3. Generate required deliverables
4. Enforce quality gates and human approvals
5. Maintain an audit trail of all decisions

## Adaptive Execution Matrix

| Request Type | Phases Executed |
|---|---|
| New feature / greenfield | 01 Inception → 02 Construction → 03 Operations |
| Enhancement (existing) | BA stage → 02 Construction → Security check |
| Bug fix | Developer → QA → Security patch check |
| Infrastructure change | Architect → DevOps |
| Security patch | Security Agent → Developer → QA |
| Performance optimization | Architect → Developer → QA → DevOps |

## Core Principles

1. **AI Proposes, Humans Approve**: Never auto-proceed past quality gates
2. **Documented Artifacts**: Every stage produces documented deliverables
3. **Ambiguity Resolution**: All uncertainties resolved via Q&A before implementation
4. **Audit Trail**: Complete audit log maintained (.kernel/artifacts/audit.md)
5. **Architecture-First**: Code never generated before architecture approval
6. **TDD Approach**: Tests written alongside code, not after deployment
7. **Security-First**: Security review runs before any deployment

## Installation

Kernel ships as both a universal agent skill (works with Claude Code, Cursor, Copilot, Codex, Windsurf, Gemini CLI, Cline, and more) **and** a native Claude Code plugin.

### Option A — Install as an agent skill (recommended, any IDE)

```bash
npx skills add sumanth-14/kernel-dlc
```

This installs the skill stub into your agent's configuration and copies `CLAUDE.md` + `.kernel/` into the current project. Activate in any conversation by prefixing your request with `Using Kernel, ...`.

### Option B — Install as a Claude Code plugin

Inside Claude Code:

```
/plugin marketplace add sumanth-14/kernel-dlc
/plugin install kernel@sumanth-14
```

You then get native slash commands: `/kernel-start`, `/kernel-status`, `/kernel-approve`, `/kernel-revise`.

### Option C — Clone manually

```bash
git clone https://github.com/sumanth-14/kernel-dlc.git
cp -r kernel-dlc/.kernel kernel-dlc/CLAUDE.md ./your-project/
```

## Usage

1. Start any request with `Using Kernel, [your goal]` — e.g. `Using Kernel, build a subscription API`.
2. Each agent stage loads its rule file from `.kernel/` automatically.
3. Artifacts are saved to `.kernel/artifacts/` as each phase completes.
4. Approve at every gate — Kernel never auto-proceeds.

## Updating

Kernel is installed statically (offline-safe, version-stable). To update:

```bash
npx skills add sumanth-14/kernel-dlc --force
```

Check the current version in the [`VERSION`](VERSION) file or release notes in [`CHANGELOG.md`](CHANGELOG.md). Update only at project boundaries — rule changes between versions can invalidate in-flight artifacts.

## Documentation

- **[CLAUDE.md](CLAUDE.md)** - Main framework definition and orchestration rules
- **[.kernel/](.kernel/)** - Detailed rules for each agent and phase
- **.kernel/artifacts/** - Execution artifacts and audit trail (generated during project runs)

## Requirements

- AI agent orchestration system (Claude, Claude Copilot, or compatible)
- Understanding of SDLC best practices
- Commitment to formal approval workflows

## Use Cases

- **Enterprise software projects** requiring formal SDLC governance
- **Cross-functional teams** coordinating multiple AI agent roles
- **Regulated industries** needing audit trails and quality gates
- **Large-scale feature development** with complex requirements
- **Security-critical systems** requiring formal reviews

## License

Licensed under MIT-0. See LICENSE file for details.

## Contributing

Contributions are welcome! Please follow the framework principles:
1. Propose changes via pull request
2. Ensure all rule files remain consistent
3. Add artifacts for any process changes
4. Update relevant documentation

## Support

For issues, questions, or improvements, please open an issue on GitHub or contact the maintainers.

---

**Version**: 1.0.0  
**Last Updated**: April 2026
