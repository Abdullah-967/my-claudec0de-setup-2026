---
description: Capture a note to the vault
argument-hint: "[decision:|project <name>:|lexicon:|idea:] <text>"
---

Capture `$ARGUMENTS` into `~/.claude/my_vault/` by prefix:

- `decision: <text>` → append to `decisions.md`: date, decision, why (extract if present), rejected (extract if present)
- `project <name>: <text>` → upsert card in `projects.md` (State + Next fields)
- `lexicon: "<term>" = <meaning>` → append to `lexicon.md`
- `idea: <text>` or bare text → new file `notes/YYYY-MM-DD-<slug>.md`

Use today's date. Confirm with one line: what was captured and where.
