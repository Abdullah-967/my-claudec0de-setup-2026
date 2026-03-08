# Claude Code Setup

A project template for AI-assisted development with Claude Code — user preferences, a docs-driven context system, and custom workflow commands.

## Structure

```
.
├── .claude/
│   ├── commands/
│   │   ├── commit.md        # Semantic commit workflow
│   │   ├── add.md           # Custom command generator
│   │   ├── note.md          # Vault capture (decisions, ideas, lexicon)
│   │   └── educate.md       # 6-phase technical teaching
│   ├── docs/
│   │   ├── index.md         # Routing hub — read this before any task
│   │   ├── architecture.md  # Stack, structure, key patterns
│   │   ├── database.md      # Schema, relationships, auth/RLS, migrations
│   │   ├── api.md           # Route map, auth conventions, error handling
│   │   └── deployment.md    # Environments, deploy steps, env vars
│   └── skills/
│       └── skill-creator/   # Skill creation workflow
├── .mcp.json                # MCP server definitions
├── CLAUDE.md                # User preferences + navigation protocol
└── HANDOFF.md               # Session handoff — updated after each feature
```

## Quick Start

### Option A: Fork and Clone

```bash
git clone https://github.com/YOUR_USERNAME/my-claude-setup.git my-project
cd my-project
```

### Option B: Copy into an existing project

```bash
git clone https://github.com/YOUR_USERNAME/my-claude-setup.git /tmp/claude-setup
cp -r /tmp/claude-setup/.claude /path/to/your/project/
cp /tmp/claude-setup/CLAUDE.md /path/to/your/project/
cp /tmp/claude-setup/HANDOFF.md /path/to/your/project/
```

## How it works

### `CLAUDE.md`
Fill in the `[placeholders]` with your stack, tools, and name. This is loaded every session — keep it lean.

### Docs system (`.claude/docs/`)
Project knowledge loaded **on demand**. Claude reads `index.md` first, then pulls only the relevant file for the task at hand.

**What belongs here:** architecture decisions, DB schema, API patterns, deployment steps, domain-specific conventions — anything too detailed for `CLAUDE.md` but needed for specific tasks.

**What doesn't belong here:** command references, skill docs, or anything Claude already knows.

Add a doc, add a row to `index.md`. That's the whole system.

### `HANDOFF.md`
Append a 1-2 sentence summary after each feature. Claude reads it at session start to recover context without re-reading the whole codebase.

### Commands

| Command | Purpose |
|---------|---------|
| `/commit` | Review changes and create a semantic commit |
| `/add <name> <desc>` | Generate a new custom slash command |
| `/note <text>` | Capture a note to `~/.claude/my_vault/` |
| `/educate <concept>` | 6-phase Socratic lesson saved as `lesson-<topic>.md` |
