# CodeWiki — Claude Code Skill

A Claude Code skill that generates a structured product knowledge base (`codewiki/`) from codebase scanning.

## What it does

CodeWiki scans your codebase, gathers product context, discovers user flows, and generates structured documentation including:

- Product overview and architecture docs
- User flow documentation (step-by-step)
- API reference and data models
- Service map and event catalog (for microservices)
- Environment variable reference
- Dev/build/test commands
- Domain glossary
- `CLAUDE.md` for Claude Code context

## Supports

- Single repos, monorepos, and multi-repo microservices
- Any tech stack (Go, Node/TS, Python, Rust, Flutter/Dart, and more)
- Incremental updates (detects existing files and offers merge)

## Installation

Copy the `codewiki` folder into your Claude Code skills directory:

```bash
cp -r codewiki ~/.claude/skills/codewiki
```

## Usage

In Claude Code, run:

```
/codewiki
```

The skill will walk you through:

1. **Product context gathering** — asks about your product, users, and URLs
2. **Codebase analysis** — scans code structure, endpoints, models, env vars
3. **User flow discovery** — identifies and documents key user journeys
4. **Architecture checkpoint** — confirms understanding before generating
5. **Knowledge base generation** — writes all docs to `codewiki/`
6. **CLAUDE.md generation** — creates or merges project context file
7. **Git & repo setup** — commits and optionally pushes to GitHub

## File Structure

```
codewiki/
├── SKILL.md              # Skill definition and instructions
└── templates/            # Output templates
    ├── architecture.md
    ├── claude-md.md
    ├── events.md
    ├── readme.md
    ├── service-map.md
    └── user-flow.md
```

## Output Structure

```
codewiki/
├── overview.md
├── architecture.md
├── service-map.md          # microservices only
├── events.md               # microservices only
├── user-flows/
│   ├── index.md
│   └── <flow-name>.md
├── api-reference.md
├── data-models.md
├── frontend-map.md         # if frontend exists
├── mobile-map.md           # if mobile app exists
├── commands.md
├── env-vars.md
└── glossary.md
```

## License

MIT
