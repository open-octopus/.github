# Contributing to OpenOctopus

Thanks for your interest in contributing! This guide covers how to get started with any repository in the [open-octopus](https://github.com/open-octopus) organization.

## Getting Started

### Prerequisites

- **Node.js** >= 22
- **pnpm** (package manager)
- **Git**

### Setup (Core Monorepo)

```bash
git clone https://github.com/open-octopus/openoctopus.git
cd openoctopus
pnpm install
pnpm build
pnpm test:unit
```

### Useful Commands

| Command | Purpose |
|---------|---------|
| `pnpm build` | Build all packages |
| `pnpm dev` | Dev mode with hot-reload |
| `pnpm test:unit` | Run unit tests |
| `pnpm typecheck` | TypeScript strict check |
| `pnpm lint` | Lint with oxlint |
| `pnpm format` | Format with oxfmt |
| `pnpm knip` | Dead code detection |
| `pnpm check` | typecheck + lint + format |

## Development Workflow

1. **Fork** the repository
2. **Create a branch** from `main` (`feat/your-feature` or `fix/your-fix`)
3. **Make your changes** with tests
4. **Run checks:** `pnpm check && pnpm test:unit`
5. **Open a Pull Request** against `main`

### Branch Naming

| Prefix | Use |
|--------|-----|
| `feat/` | New feature |
| `fix/` | Bug fix |
| `docs/` | Documentation only |
| `refactor/` | Code restructuring |
| `test/` | Adding or updating tests |
| `chore/` | Build, CI, tooling |

## Code Style

- **TypeScript strict mode** — no `any`, no implicit types
- **oxlint** for linting, **oxfmt** for formatting
- **Vitest** for tests, colocated next to source (`*.test.ts`)
- **Zod** for runtime validation
- IDs use the format `{prefix}_{uuid}` (e.g. `realm_abc123`)

## Terminology

The five core terms are **always written in English**, even in comments or docs written in other languages:

| Term | Meaning |
|------|---------|
| **Realm** | Autonomous life domain (pet, finance, health, etc.) |
| **Entity** | Object within a Realm (living, asset, organization, abstract) |
| **Summon** | Transform an Entity into a living AI Agent |
| **Agent** | AI agent — Central, Realm, or Summoned tier |
| **Skill** | Capability available to Agents (global or realm-scoped) |

## Monorepo Packages

```
packages/
  shared/    — types, errors, IDs, logger, config
  storage/   — SQLite, migrations, JSONL sessions
  core/      — realm manager, agent runner, LLM providers
  summon/    — SOUL.md parser, prompt compiler
  channels/  — Telegram, Discord, Slack adapters
  ink/       — Express + WebSocket gateway
  tentacle/  — CLI tool
  realmhub/  — package registry client
  dashboard/ — web UI
```

Dependency flow: `shared -> storage, core -> summon, channels -> ink -> tentacle`

## Submitting Issues

- **Bug reports:** Use the bug report template
- **Feature requests:** Use the feature request template
- **Realm ideas:** Use the realm package request template
- **Questions:** Join [The Reef on Discord](https://discord.gg/openoctopus)

## Code of Conduct

All contributors are expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
