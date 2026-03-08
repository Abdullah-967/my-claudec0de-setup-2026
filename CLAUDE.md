# User Preferences

## About

- Name: [Your Name]
- Platform: [OS + shell, e.g. Windows 11, Git Bash]

## Coding Style

- Keep code minimal and clean
- Comments explain "why," not "what"
- Prefer established libraries over custom implementations
- Type hints in Python, strict TypeScript

## Preferences

- Language: [e.g. Python 3.12+, TypeScript]
- Framework: [e.g. Next.js 15 App Router]
- Package manager: [e.g. uv (Python), npm (Node)]
- Testing: [e.g. pytest, vitest]
- Linting: [e.g. ruff, biome]

## Git Workflow

- Branch naming: `type/short-description` (e.g. `feat/auth-flow`, `fix/api-timeout`)
- Prefer small, focused commits over large ones
- Don't commit unless asked

## Communication

- Be concise — no filler, no preambles
- When presenting options, give a recommendation with reasoning
- When stuck or uncertain, say so immediately rather than guessing
- **If a request is ambiguous or unclear, stop and ask targeted questions before acting**
- Use plan mode for non-trivial tasks
- Never include time estimates, durations, or period-based roadmaps

## Error Handling

- Surface errors early, fail fast
- Log with structured context, not bare messages
- Don't add defensive error handling for impossible cases

## MCP Config

- MCP servers go in `.mcp.json` (project root) or `~/.claude.json` — never in `settings.local.json` (permissions only)

## Tools

- **Note**: `/note` — capture notes to the vault
- [Add your MCP tools and skills here]

## Browser QA Protocol

**Applies when:** browser-testing or UI verification via Playwright.

- Act as a senior full-stack engineer. Navigate methodically, read console errors, inspect snapshots.
- **Never skip, suppress, or retry-loop past errors.** Every error is a signal — trace it to source.
- **Small/medium fixes** (wrong routes, missing props, styling, null checks): fix immediately, re-test.
- **Major fixes** (architecture, migrations, >3 files): present findings and proposed fix first.

# My Vault

Personal knowledge base at `~/.claude/my_vault`. Start with `index.md` — it tells you what's here and when to read each file. This is persistent context (decisions, project state, terminology), not rules.

# Navigation Protocol

BEFORE starting any task:

1. Read `.claude/docs/index.md` — infer where to find relevant information
2. Read ONLY the matched file(s)
3. **Never** retrieve all `.md` files in one call
4. For multi-domain tasks, check the Combos table for pre-mapped file sets
5. If nothing resonates, work from the codebase directly
6. If information exists in a doc but isn't reflected in `index.md`, add it there concisely

# HANDOFF.md

- Summarize each completed feature in 1-2 sentences
- Update at the end of each feature implementation
