# Governance

AgentForge is governed on paper, in the open: a constitution for principles, ADRs for architecture, RFCs for proposals, standards for practice, small sprints for progress.

## Decision stack

| Layer | Purpose |
|---|---|
| Constitution | Durable principles that outlive decisions |
| Charter | Scope: what the project is and is not |
| Vision | Direction of travel |
| ADRs | Architecture decision records (`adrs/`) |
| RFCs | Proposals for new work (`agentforge-community`) |
| Standards | Required practice (engineering, documentation) |
| Requirements | What a feature must do, before it is built |
| Milestones | Releasable units with exit criteria |

## Sprint model

Each Genesis sprint ships as a milestone:

1. Issues: requirements, boundary decision, implementation, CI validation, docs and release
2. Requirements before implementation
3. ADR with or before the code
4. Offline, deterministic tests; CI must pass
5. `Genesis-0.0.x` release; issues close with references

18 sprints shipped and counting.

## Community

Governance templates (ADR/RFC templates, code of conduct, contributing, security) live org-wide in the `.github` repository. Proposals and RFCs live in `agentforge-community`.
