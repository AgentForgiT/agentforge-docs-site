# Contributing

AgentForge is an open engineering platform for agentic AI systems. Contributions — code, docs, research, and integrations — follow the same governance hierarchy as the project itself.

## Start here

1. Run the gateway locally ([Getting Started](getting-started.md)).
2. Read [Governance](governance.md) to understand how decisions are made.
3. Read the **[community overview](https://github.com/AgentForgiT/agentforge/blob/main/docs/community.md)** — contribution paths, the release train, and the public `0.1.0` gate.
4. Open an issue describing what you want to do — or pick one that interests you.

## Requirements

- **Boundaries respected.** Code lives in the module that owns it.
- **Tests offline and deterministic.** No network, no credentials, no live providers.
- **Docs updated with code.** Same commit.
- **Validation green** (from the repository root):

```bash
python scripts/validate_bootstrap.py
python scripts/validate_aics.py
python -m unittest discover -s apps/cli/tests
python -m unittest discover -s apps/gateway/tests
python -m unittest discover -s apps/sdk/tests
git diff --check
```

## Commits

Conventional prefixes (`feat:`, `fix:`, `test:`, `docs:`, `chore:`) with a body that explains what and why. Small, reviewable commits.

## The live platform

The website runs on AgentForge — you can try everything it ships:

- [Playground](playground.html) — talk to a local gateway, streaming live
- [AICS Validator](aics-validator.html) — validate a context in your browser
- [Compatibility](compatibility.html) — which tool works with which provider
- [Providers](providers.html) — browse a live gateway's models
- [Benchmarks](benchmarks.html) — observe latency and throughput
- [Twin](twin.html) — the AgentForge engineering twin

## The 0.1.0 gate

Genesis ends at `0.0.32`. The public `0.1.0` line is gated by six verifiable exit criteria (DEC-0006) — see the [release-gate checklist](https://github.com/AgentForgiT/agentforge/blob/main/.agentforge/requirements/0.1.0-release-gate-checklist.md). Contributions land against that frame.
