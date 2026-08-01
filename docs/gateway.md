# Gateway

The gateway (`apps/gateway`) is a dependency-free Python HTTP service exposing an OpenAI-compatible surface:

- `GET /health`
- `GET /v1/models`
- `POST /v1/chat/completions` — JSON and SSE streaming

## Boundaries

Every gateway boundary is recorded in an ADR:

| Boundary | ADR | Owns |
|---|---|---|
| Provider adapters | ADR-0008 | provider-specific transport, auth, JSON parsing, error translation |
| Provider contract tests | ADR-0009 | offline, deterministic provider verification |
| Request validation | ADR-0010 | model/messages/stream validation |
| Error contract | ADR-0011 | standard JSON error envelope and status mapping |
| Response normalization | ADR-0012 | minimal response/chunk shape, public model alias |
| Configuration validation | ADR-0013 | strict config parsing with defaults |
| Streaming | ADR-0014 | OpenAI-compatible SSE, gateway-owned chunk normalization |
| Logging | ADR-0015 | structured access records, configurable level, privacy rules |

## Request validation

Required fields: `model` (must be registered), non-empty `messages`, optional boolean `stream`. Non-boolean `stream` values are rejected.

## Error contract

All errors use a standard envelope:

```json
{"error": {"message": "not found", "type": "not_found"}}
```

Status mapping: `400` bad request, `404` unknown model/route, `500` provider configuration/internal, `502` upstream provider.

## Response normalization

Successful responses and streaming chunks pass through the gateway normalizer, which validates minimal shape and sets the public model alias. Malformed provider output becomes an upstream provider error. Providers translate; the gateway normalizes.

## Configuration

```json
{
  "server": {"host": "127.0.0.1", "port": 8080, "log_level": "INFO"},
  "models": {"mock-coder": {"provider": "mock", "provider_model": "mock-coder-v1"}},
  "providers": {"mock": {"type": "mock"}}
}
```

Validation covers root shape, server host/port/log_level, model fields, provider fields, timeouts, headers, and model-provider references. Defaults: host `127.0.0.1`, port `8080`, level `INFO`, mock provider.

## Logging

- Access records: `method`, `path`, `status`, `duration_ms`
- Chat context records: `model`, `stream` flag (after validation)
- Unexpected handler errors: `ERROR` with `500` record; exception details log-only
- **Never logged:** request bodies, response bodies, headers, credentials

## Run tests

```bash
python -m unittest discover -s apps/gateway/tests
```

The suite is offline and deterministic — no network, no credentials, no live providers.
