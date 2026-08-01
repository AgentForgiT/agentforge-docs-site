# AICS

The AI Context Specification (AICS) defines **portable project context that humans and AI tools both read**: a `.agentforge/` directory at a repository root, written in plain Markdown, validated by the CLI.

## Required structure

```text
.agentforge/
├── vision.md          # why the project exists
├── charter.md         # scope and boundaries
├── constitution.md    # durable principles
├── architecture.md    # how the system is built
├── tech-stack.md      # what it is built with
├── roadmap.md         # where it is going
├── milestones.md      # how progress is measured
├── glossary.md        # shared vocabulary
├── repo-map.md        # where things live
├── backlog.md         # what is queued
├── decisions.md       # decision register
├── adrs/              # architecture decision records
├── decisions/         # decision records
├── requirements/      # requirement documents
├── specs/             # specifications
├── standards/         # engineering and documentation standards
└── agents/            # per-agent instruction files
```

## Adoption levels

1. **Present** — context directory exists, core files readable
2. **Governed** — decisions, standards, and requirements follow prescribed structure
3. **Validated** — passes the CLI's structural and metadata checks

## Agent integration

Per-agent instruction files in `.agentforge/agents/` wire AI tools to the context: Codex, Claude, Kiro, Gemini, Copilot, OpenCode, OpenClaw, and AION are supported today. The spec is open — any tool can implement it.

## Specification documents

- `specs/aics-v0.1.md` — the specification
- `specs/aics-validation-v0.1.md` — validation rules and adoption levels

## Tooling

```bash
agentforge validate-context
agentforge init-context
agentforge explain-context
agentforge doctor
```
