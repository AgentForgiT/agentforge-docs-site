# Website: IDE / Tool Compatibility Matrix

| | |
|---|---|
| Status | Draft |
| Sprint | Genesis Sprint 22 (Website quick-win) |
| Related | Epic 8 (Website), `.agentforge/backlog.md` |
| Sources | Live-verified data from Sprint 19 (OpenRouter) and Sprint 20 (Ollama); public tool documentation (Codex CLI `config.toml`, OpenCode providers, Cursor/Claude Code settings) |

## Purpose

The Compatibility Matrix answers the question visitors actually have: "If I use tool X, which providers can I connect — and how?" It is the flagship differentiator identified in the Epic 8 vision: AgentForge has the live-verified interoperability data (Sprint 19 OpenRouter, Sprint 20 Ollama) and a working OpenAI-compatible gateway that any compatible tool can route through.

## Requirements

R1. The matrix lists AI coding tools (rows) × provider families (columns): OpenAI, Anthropic, Gemini, OpenRouter, Ollama/local, and the AgentForge Gateway.
R2. Every cell states honest status: **native** (tool supports provider out of the box), **via config** (supported with a documented configuration change), **needs adapter** (no native support; a bridge is required), or **not supported** (no path today).
R3. Every "via config" and "needs adapter" claim must trace to a public, citable source (tool docs, GitHub issues, official guides) or to AgentForge's own live verification. No invented compatibility claims.
R4. The page is interactive: filter by tool or provider family, and expand any tool row to reveal the exact configuration snippet for routing that tool through the AgentForge Gateway.
R5. The page matches the flagship visual language (dark, serif + mono, forge accents) and lives in the docs site alongside the playground and validator.
R6. The AgentForge Gateway row/column is clearly marked as the recommended unification path, with a copyable config example.

## Verified Fact Base (as of 2026-08-01)

| Tool | Protocol / mechanism | Verified source |
|---|---|---|
| Claude Code | Anthropic Messages API via `ANTHROPIC_BASE_URL`; not OpenAI-compatible natively | GitHub issue anthropics/claude-code#216; claudeapi.com guide |
| Codex CLI | Custom providers via `~/.codex/config.toml` `[model_providers.*]`; OpenRouter + Ollama `http://localhost:11434/v1` both documented | openrouter.ai blog; morphllm.com; medium superagentic-ai |
| OpenCode | Custom providers via `opencode.json` with `npm: "@ai-sdk/openai-compatible"` + `baseURL` | opencode.ai/docs/providers |
| Cursor | OpenAI-compatible custom endpoint ("Override OpenAI Base URL") | claudeapi.com guide |
| Cline | OpenAI-compatible mode or Anthropic mode with custom base URL | claudeapi.com guide |
| AgentForge Gateway | OpenAI-compatible `/v1`; providers: mock, ollama (keyless), openrouter | AgentForge ADR-0017/0018, Sprint 19/20 live verification |

## Acceptance Criteria

- [ ] Page serves at `/compatibility.html` on the public docs site
- [ ] Matrix renders with all six provider columns and at least five tool rows
- [ ] All compatibility claims link to a cited source or AgentForge live verification
- [ ] Filter and row-expansion interactions work in a live browser
- [ ] `mkdocs build --strict` passes
