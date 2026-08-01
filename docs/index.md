# AgentForge

Open engineering platform for agentic AI systems.

- **Gateway** — a dependency-free, OpenAI-compatible local gateway with streaming, provider adapters, and structured logging
- **CLI** — validate, scaffold, explain, and diagnose AI Context Specification (AICS) contexts
- **AICS** — an open specification for portable project context that humans and AI tools both read

## Quick start

```bash
cd apps/gateway
python -m agentforge_gateway.cli --config config.example.json
```

```bash
curl http://127.0.0.1:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "mock-coder", "messages": [{"role": "user", "content": "Hello"}]}'
```

No keys. No network. The default config uses the deterministic mock provider.

## Project state

Genesis: 18 sprints shipped, each released as a `Genesis-0.0.x` milestone with requirements, ADR, implementation, tests, CI validation, and release notes. Every architecture decision is recorded as an ADR; the monorepo's own context passes AICS validation in CI on every push.

## Where to go next

| You want to... | Go to |
|---|---|
| Run the gateway | [Getting Started](getting-started.md) |
| Understand the gateway's boundaries | [Gateway](gateway.md) |
| Use the CLI | [CLI](cli.md) |
| Read the context spec | [AICS](aics.md) |
| Understand how decisions are made | [Governance](governance.md) |
| Contribute | [Contributing](contributing.md) |
| Read the narrative handbook | [agentforge-handbook](https://github.com/AgentForgiT/agentforge-handbook) |
