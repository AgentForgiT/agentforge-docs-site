# SDK

The AgentForge SDK (`agentforge-sdk`) is a **dependency-free Python client** for the gateway (ADR-0025). It covers both gateway surfaces — OpenAI Chat Completions and Anthropic Messages — with streaming and auth, using only the standard library.

## Install

```bash
pip install agentforge-sdk
```

Until the PyPI publication step is completed (see the [0.1.0 release gate](https://github.com/AgentForgiT/agentforge/blob/main/.agentforge/requirements/0.1.0-release-gate-checklist.md)), install directly from the release wheel:

```bash
pip install https://github.com/AgentForgiT/agentforge/releases/download/Genesis-0.0.30/agentforge_sdk-0.0.1-py3-none-any.whl
```

## Usage

```python
from agentforge_sdk import AgentForgeClient

client = AgentForgeClient("http://127.0.0.1:8080", api_key="optional")

client.health()   # {"status": "ok", ...}
client.models()   # {"data": [{"id": "mock-coder"}, ...]}

# OpenAI surface
client.chat_completions("mock-coder", [{"role": "user", "content": "Hi"}])

# streaming
for chunk in client.chat_completions("mock-coder", [{"role": "user", "content": "Hi"}], stream=True):
    print(chunk)

# Anthropic Messages surface
client.anthropic_messages("mock-coder", [{"role": "user", "content": "Hi"}])
```

## Auth

Pass `api_key` when the gateway runs with `server.api_key_env` set (ADR-0023). The SDK sends `Authorization: Bearer <key>` and never logs it.

## Errors

Gateway error envelopes raise `AgentForgeError(status, body)` with the status and the parsed envelope.

## Properties

- **Stdlib only** — `urllib.request` + `json`; no dependencies.
- **Thin client** — the gateway owns validation, normalization, and protocol translation; the SDK only speaks HTTP.
- **Offline-testable** — injected transport (the gateway's own contract-test pattern, ADR-0009).
