# Contributing

## Start here

1. Run the gateway locally ([Getting Started](getting-started.md)).
2. Read [Governance](governance.md) to understand how decisions are made.
3. Open an issue describing what you want to do — or pick one that interests you.

## Requirements

- **Boundaries respected.** Code lives in the module that owns it.
- **Tests offline and deterministic.** No network, no credentials, no live providers.
- **Docs updated with code.** Same commit.
- **Validation green** (from the repository root):

```bash
python scripts/validate_bootstrap.py
python scripts/validate_aics.py
python -m unittest discover -s apps/cli/tests
python -m unittest apps.cli.tests.test_install
python -m unittest discover -s apps/gateway/tests
git diff --check
```

## Commits

Conventional prefixes (`feat:`, `fix:`, `test:`, `docs:`, `chore:`) with a body that explains what and why. Small, reviewable commits.

## RFCs

Cross-cutting proposals (new specifications, new modules, public API changes) start as RFCs in `agentforge-community`. Templates live org-wide in `.github`.

## License

Contributions are accepted under the MIT license, matching the repositories they land in.
