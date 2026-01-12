# Project Memory & Rules

## 1. Operating Protocol (The "Sync" Flow)
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

## 3. The "Shift-End" Protocol
Before terminating a session, you MUST leave the project ready for the next "shift":
1. **Update `features.json`**: Set the current feature to `passes: true`.
2. **Update `HANDOFF.md`**:
   - `Current State`: Summary of what was achieved.
   - `Technical Debt/Blockers`: Any issues the next agent should know about.
   - `Next Step`: The specific atomic task for the next session.
3. **Commit**: Finalize work with a descriptive commit message linking to the feature ID.

## 4. Critical Commands
- **Initialization**: `./init.sh`
- **Checklist Status**: `cat features.json`
- **Context Refresh**: `/sync` (Custom Command)
- **Primary Test Suite**: `npm test` (or project-specific equivalent)