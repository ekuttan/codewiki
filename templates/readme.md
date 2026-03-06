# <Product Name> — CodeWiki

> Product knowledge base for LLM-assisted development

This repository contains structured documentation designed to give LLMs (and humans)
the context needed to contribute code effectively to **<Product Name>**.

## Quick Setup

### 1. Clone all repos into a single parent folder

```bash
mkdir -p ~/projects/<product-name> && cd ~/projects/<product-name>

# Clone this documentation repo
git clone <codewiki-repo-url>

# Clone source repos
git clone <repo-url> <folder-name>
```

### 2. Using with Claude Code

Copy CLAUDE.md into whichever repo you're working in:
```bash
cp <codewiki-folder>/CLAUDE.md <target-repo>/CLAUDE.md
```

Or point Claude to the full wiki:
```
Read the knowledge base in ../<codewiki-folder>/codewiki/ before making changes.
```

## What's Inside

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project context for Claude Code |
| `codewiki/overview.md` | Product overview, target users, links |
| `codewiki/architecture.md` | System architecture and tech stack |
| `codewiki/service-map.md` | Service dependencies and communication |
| `codewiki/events.md` | Async event catalog and flow chains |
| `codewiki/user-flows/` | Step-by-step user flow documentation |
| `codewiki/api-reference.md` | API endpoints (external + internal) |
| `codewiki/data-models.md` | Database schemas and relationships |
| `codewiki/commands.md` | Dev, test, build, deploy commands |
| `codewiki/env-vars.md` | Environment variable reference |
| `codewiki/glossary.md` | Product-specific terminology |

> Remove rows for files that were not generated.

## Source Repos

| Repo | Description | Stack |
|------|-------------|-------|
| [<n>](<url>) | <description> | <tech stack> |

## Updating

Run CodeWiki again from the parent folder. It will detect existing files and offer to merge or replace.
