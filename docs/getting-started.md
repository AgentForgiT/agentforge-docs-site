# Getting Started

## Run the gateway

```bash
cd apps/gateway
python -m agentforge_gateway.cli --config config.example.json
```

```text
AgentForge Gateway listening on http://127.0.0.1:8080
```

### Chat completion (JSON)

```bash
curl http://127.0.0.1:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "mock-coder", "messages": [{"role": "user", "content": "Write a Python function."}]}'
```

### Chat completion (streaming)

```bash
curl -N http://127.0.0.1:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "mock-coder", "stream": true, "messages": [{"role": "user", "content": "Write a Python function."}]}'
```

The response is an SSE stream (`text/event-stream`) with OpenAI-compatible chunks ending in `data: [DONE]`.

### Health and models

```bash
curl http://127.0.0.1:8080/health
curl http://127.0.0.1:8080/v1/models
```

## Use a real provider

1. Copy `apps/gateway/config.openrouter.example.json` to your own config.
2. Export `OPENROUTER_API_KEY`.
3. Start the gateway with `--config` pointing at your config.
4. Request model `openrouter-coder` — the gateway forwards to the provider and normalizes the response.

## Install the CLI

```bash
cd apps/cli
pip install -e .
agentforge validate-context
```

## Logs

Access records stream to stderr under the `agentforge.gateway` logger:

```text
INFO method=POST path=/v1/chat/completions status=200 duration_ms=3
```

Set `server.log_level` in the config to `DEBUG`, `WARNING`, or `ERROR` (default `INFO`). Request bodies, headers, and credentials are never logged.
