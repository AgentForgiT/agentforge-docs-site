# AgentForge Docs Site

Published reference documentation for the AgentForge platform, built with MkDocs and deployed to GitHub Pages.

**Live site:** <https://agentforgit.github.io/agentforge-docs-site/>

## Content

| Page | Covers |
|---|---|
| Getting Started | run the gateway, streaming, real providers, CLI install |
| Gateway | boundaries (ADRs), validation, errors, normalization, config, logging |
| CLI | commands, boundaries, install, tests |
| AICS | the AI Context Specification |
| Governance | decision stack, sprint model |
| Contributing | requirements, validation, commits, RFCs |

The narrative companion — the *why* behind the project — lives in the [agentforge-handbook](https://github.com/AgentForgiT/agentforge-handbook).

## Build locally

```bash
pip install -r requirements.txt
mkdocs serve
```

## Deploy

Pushing to `main` builds the site with `mkdocs build --strict` and deploys via GitHub Actions to Pages. Manual deploys: `workflow_dispatch`.
