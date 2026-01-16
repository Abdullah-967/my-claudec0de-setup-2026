# Project Memory & Rules

## 1. Operating Protocol (The "Sync" Flow)
- **Context Default:** When uncertain about project state, decisions, or implementation approach, ALWAYS read `features.json` and `HANDOFF.md` first. These are the authoritative sources of truth for what has been done and what needs doing.
- **State Discovery:** At the start of every session (or when `/sync` is called), you MUST:
    1. Run `ls -R` to map the current repository structure.
    2. Read `features.json` to identify the current feature checklist.
    3. Read `HANDOFF.md` to recover the narrative context from the last agent.
    4. **Git Context:** Run `git log --oneline -10` to see actual code changes and `git status` to check for uncommitted work.
    5. **Environment:** Execute `./init.sh` to ensure the dev server and dependencies are active.
- **Task Execution:** Work on exactly ONE atomic feature from `features.json` at a time.
- **Verification:** Only mark a feature as `passes: true` after running its specific test command. Use browser automation for visual verification of UI changes.

## 2. Engineering Standards
- **Git Worktrees:** For complex features or parallel tasks, create a dedicated Git worktree to isolate the environment and maintain a clean state.
- **Atomic Commits:** Make a Git commit immediately after a feature is verified and `features.json` is updated.
- **No-Clutter Rule:** Do not modify files outside the current feature scope unless refactoring is explicitly requested.
- **Verification Gate**: A feature is ONLY "Complete" when:
  1. The specific tests of this feature return 0 exit code.

## 3. The "Shift-End" Protocol
Before terminating a session, you MUST leave the project ready for the next "shift":
1. **Update `features.json`**: Set the current feature to `passes: true`.
2. **Update `HANDOFF.md`**:
   - **INSERT** a new session entry at the TOP of HANDOFF.md with:
     - `## Session [DATE] - [FEATURE_ID]`
     - What was implemented/achieved
     - Any blockers or debt introduced
   - **Concise Writing Rules** (keep entries scannable, not verbose):
     - Use bullet points, not paragraphs
     - List files changed with one-line descriptions: `path/file.py - added X`
     - For decisions, state the choice made, not the reasoning process
     - Blockers/debt: one line each, actionable
     - Max 8-10 lines per session entry (excluding file lists)
     - Omit filler words; write in telegram style when possible
   - The `Next Step` section at the bottom should be updated to reflect the next feature.
3. **Commit**: Finalize work with a descriptive commit message linking to the feature ID.

## 4. Critical Commands
- **Initialization**: `./init.sh` (Linux/Mac) or `init.bat` (Windows)
- **Checklist Status**: `cat features.json`
- **Context Refresh**: `/sync` (Custom Command)
- **Primary Test Suite**: `npm test` (or project-specific equivalent)

