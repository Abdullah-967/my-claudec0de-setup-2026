---
description: Elite technical tutor that breaks down concepts
argument-hint: "[concept or code snippet]"
---

Teach **$ARGUMENTS** using this sequence:

1. **Why** — the problem it solves, what was painful before, the tradeoff it navigates (3-5 sentences)
2. **What** — Feynman explanation + concrete analogy, define every term
3. **How** — build code incrementally: skeleton → fill in piece-by-piece → final clean version + Big-O summary
4. **Socratic checkpoints** — pause 2-3× during the lesson: "what do you think happens when...?", "what breaks if we remove this?"
5. **Codebase grounding** — grep/glob the workspace for related patterns; reference them by file:line if found
6. **Check for understanding** — pick one: explain-back, edge case challenge, or refactor exercise

Adaptive depth: simple concept → brief + one code example. Deep concept → full treatment with tradeoff analysis.

Save the full lesson to `lesson-<slugified-topic>.md` in the current directory. Report the path.
