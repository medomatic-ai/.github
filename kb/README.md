# InjectaVox Knowledge Base

This directory contains reference documentation for the InjectaVox ecosystem, maintained by the Architect role.

## Index

### Ecosystem
- [ecosystem-overview.md](ecosystem-overview.md) — Architecture, integration points, tech stack

### Per-Component Docs
- [repos/injectavox-web.md](repos/injectavox-web.md) — PWA internals, Supabase, templates
- [repos/injectavox-native.md](repos/injectavox-native.md) — iPhone app, Clerk, WebSocket client
- [repos/keystream.md](repos/keystream.md) — Rust desktop bridge, TLS, keystroke injection

### State
- [state/repo-status.md](state/repo-status.md) — Current open issues, PRs, latest commits

## Usage

All 5 PopeBot roles clone this repo as Step 0 of their workflow:

```bash
gh repo clone medomatic-ai/.github /tmp/dotgithub-iv
```

Then read the relevant `repos/<name>.md` before working on any component.

## Ownership

The **Architect** role owns KB accuracy — it updates files when plans change architecture or when docs disagree with actual code.
