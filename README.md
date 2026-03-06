# CodeWiki

**Turn any codebase into a structured knowledge base that Claude actually understands.**

You just joined a new project. Or maybe you've been on it for a year but Claude keeps asking you the same questions. It doesn't know your auth flow. It doesn't know which service talks to which. It doesn't know that "pattukal" means songs in your domain.

CodeWiki fixes that. One command, and your entire codebase becomes a structured wiki that gives Claude (and your team) the full picture.

---

## The Problem

Claude Code is powerful, but it starts every conversation blind. It reads files on demand, guesses at architecture, and misses the connections between services. The result:

- **Repeated context-setting.** You explain the same auth flow, the same data model, the same deployment setup — every single session.
- **Shallow understanding.** Claude sees individual files but misses how they fit together. It doesn't know your API gateway routes to three backend services, or that a webhook triggers an async chain across four of them.
- **No product awareness.** Code structure alone doesn't tell Claude who your users are, what they're trying to do, or why that edge case matters.
- **CLAUDE.md is manual and fragile.** Writing it by hand means it's always incomplete, always outdated, and never covers the full system.

## What CodeWiki Does

CodeWiki is a [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code/slash-commands) that scans your codebase and generates a complete product knowledge base. Not just code docs — product docs. It understands your architecture, traces your user flows, maps your services, and writes it all down in a format optimized for LLM consumption.

Run `/codewiki` and get:

| Output | What's in it |
|--------|-------------|
| `overview.md` | Product summary, target users, key links |
| `architecture.md` | System design, components, how they connect |
| `service-map.md` | Service dependencies, sync/async communication |
| `events.md` | Event catalog with full async flow chains |
| `user-flows/` | Step-by-step journeys mapped to actual code paths |
| `api-reference.md` | Every endpoint, grouped and documented |
| `data-models.md` | Schemas, relationships, ownership |
| `frontend-map.md` | Routes, components, state management |
| `mobile-map.md` | Screens, navigation, platform-specific patterns |
| `commands.md` | Dev, build, test, deploy — all in one place |
| `env-vars.md` | Every environment variable across every service |
| `glossary.md` | Domain-specific terms your team uses |
| `CLAUDE.md` | Auto-generated project context file |

It skips what doesn't apply. No mobile app? No `mobile-map.md`. Not microservices? No `service-map.md` or `events.md`.

## Who It's For

- **Solo devs** who want Claude to stop asking "what framework is this?" every session
- **Teams onboarding new engineers** who need to understand the system fast
- **Multi-repo projects** where no single person holds the full architecture in their head
- **Microservice architectures** where the async event chains are the hardest thing to document and the easiest thing to get wrong
- **Anyone maintaining a CLAUDE.md by hand** and tired of it being perpetually incomplete

## How It Works

CodeWiki runs in 7 phases. You don't need to manage them — just answer a few questions and let it work.

1. **Product context** — Asks about your product, users, and URLs. Fetches landing pages and docs for additional context. (Skippable — it'll infer from code and ask you to confirm.)
2. **Codebase scan** — Reads your code structure, entry points, routes, endpoints, models, env vars, and build commands. For multi-repo, it scans one repo at a time to stay within context limits.
3. **User flow discovery** — Proposes flows it found in the code, asks you to confirm or add more, then traces each flow through frontend, backend, and async side-effects.
4. **Architecture checkpoint** — Presents its understanding for you to verify before generating anything.
5. **Knowledge base generation** — Writes everything to `codewiki/` using structured templates.
6. **CLAUDE.md** — Generates a new one or merges into your existing one (your manual additions are preserved).
7. **Git setup** — Commits locally. Optionally creates a GitHub repo and pushes.

### Works with any stack

Go, TypeScript, Python, Rust, Flutter/Dart, Ruby, Java, and anything else with readable dependency files and entry points. It adapts its scanning to whatever it finds.

### Works at any scale

| Project type | How CodeWiki handles it |
|-------------|------------------------|
| Single app | Full deep scan in one pass |
| Monorepo | Scans each package/workspace, maps shared dependencies |
| Multi-repo microservices | Sequential scan with context management — infrastructure first, then gateway, frontends, core services, supporting services |

For microservices, it builds a full service topology from your infrastructure configs (docker-compose, k8s manifests, API gateway configs) before scanning individual services. It traces async event chains across services and confirms them with you.

---

## Installation

### Option 1: Clone into your skills directory

```bash
git clone https://github.com/ekuttan/codewiki.git ~/.claude/skills/codewiki
```

### Option 2: Copy manually

```bash
# Download or clone anywhere, then copy
cp -r codewiki ~/.claude/skills/codewiki
```

The skill directory should look like:

```
~/.claude/skills/codewiki/
├── SKILL.md
└── templates/
    ├── architecture.md
    ├── claude-md.md
    ├── events.md
    ├── readme.md
    ├── service-map.md
    └── user-flow.md
```

### Verify installation

Open Claude Code and type `/codewiki`. If it appears in the slash command menu, you're set.

> New to Claude Code skills? See the [official docs on extending Claude with skills](https://docs.anthropic.com/en/docs/claude-code/slash-commands).

---

## Usage

```
cd your-project
/codewiki
```

For multi-repo projects, `cd` into the parent folder that contains all your repos:

```
cd ~/projects/my-product    # contains backend/, frontend/, mobile/, etc.
/codewiki
```

### Re-running

Run `/codewiki` again anytime. It detects existing files and offers to:
- **Fresh scan** — back up and replace everything
- **Rescan & merge** — preserve your manual edits and update generated sections

---

## Customizing

### Modify templates

The `templates/` directory contains the structure for each output file. Edit them to match your team's documentation style, add sections, or remove ones you don't need.

### Modify the skill behavior

Edit `SKILL.md` to change how CodeWiki scans, what questions it asks, or how it handles specific project types. The entire skill is a single markdown file — no build step, no dependencies.

### Project-level installation

Want CodeWiki available only for a specific project? Put it in your project's plugin directory instead:

```
your-project/.claude/skills/codewiki/
```

> Learn more about skill scoping and plugin configuration in the [Claude Code settings docs](https://docs.anthropic.com/en/docs/claude-code/settings).

---

## Output Example

After running on a multi-component project, your repo will contain:

```
your-project/
├── CLAUDE.md                  # auto-generated project context
├── codewiki/
│   ├── overview.md
│   ├── architecture.md
│   ├── user-flows/
│   │   ├── index.md
│   │   ├── sign-up-onboarding.md
│   │   ├── checkout.md
│   │   └── ...
│   ├── api-reference.md
│   ├── data-models.md
│   ├── frontend-map.md
│   ├── commands.md
│   ├── env-vars.md
│   └── glossary.md
├── src/
└── ...
```

Every future Claude Code session in this project starts with full context. No more explaining your architecture from scratch.

---

## License

MIT
