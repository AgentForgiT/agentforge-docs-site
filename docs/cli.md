# CLI

The CLI (`apps/cli`) is the command surface for AICS contexts.

## Commands

| Command | Purpose |
|---|---|
| `agentforge validate-context` | Structural and metadata validation of a context |
| `agentforge init-context` | Scaffold a new context from packaged templates (never overwrites) |
| `agentforge explain-context` | Read-only orientation report of a context |
| `agentforge doctor` | Local context health diagnostics |

## Examples

```bash
# validate the current directory's context
agentforge validate-context

# scaffold a context in a new project
agentforge init-context --directory my-project

# orientation report
agentforge explain-context

# health diagnostics
agentforge doctor
```

## Boundaries

- ADR-0003 — canonical CLI architecture and shared validation boundary
- ADR-0004 — packaging (editable install first, PyPI later)
- ADR-0005 — scaffolding strategy (packaged templates, safe no-overwrite init)
- ADR-0006 — explanation boundary (read-only orientation, validation-informed status)
- ADR-0007 — doctor diagnostics boundary (read-only health checks)

## Install

```bash
cd apps/cli
pip install -e .
```

## Run tests

```bash
python -m unittest discover -s apps/cli/tests
python -m unittest apps.cli.tests.test_install
```
