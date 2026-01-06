# Claude Code Project Setup

A sophisticated project template for autonomous AI coding with Claude Code, featuring persistent memory, feature tracking, and custom workflow commands.

## Overview

This setup transforms Claude Code into a powerful autonomous development environment with:

- **Persistent Memory**: Context preservation across sessions via `HANDOFF.md`
- **Feature-Driven Development**: Structured task tracking with `features.json`
- **Smart Workflows**: Custom commands for sync, commit, and command generation
- **Git Integration**: Automatic tracking of code changes and work state
- **MCP Server Access**: Built-in documentation for Claude Code and Agent SDK

Perfect for complex projects where you need Claude to maintain context across multiple sessions and work autonomously on well-defined features.

## Features

- **Session Continuity**: Never lose context between sessions with the Sync Flow protocol
- **Atomic Workflow**: One feature at a time, with verification before moving forward
- **Smart Commits**: Semantic commit messages with conventional commits format
- **Custom Commands**: `/sync`, `/commit`, `/add` for common workflows
- **Extensible**: Easy to add new commands and adapt to your project needs
- **Git-Aware**: Automatically tracks uncommitted work and recent changes
- **Clean Handoffs**: "Shift-End Protocol" ensures the next session starts with full context

## Quick Start

Choose your setup method:

### Option A: Fork and Clone (Recommended)

The easiest way to get started:

```bash
# 1. Fork this repository on GitHub
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/my-claude-setup.git my-project
cd my-project

# 3. Customize for your project (see below)
# 4. Start using /sync
```

**Benefits:**
- All custom commands (`.claude/commands/`) pre-configured
- Directory structure already set up
- MCP server configuration included
- Just customize and start coding

**Next steps:** See "Customize for Your Project" below.

---

### Option B: One-Shot Automated Setup

For setting up in an **existing project** or **starting from scratch**, use this initialization prompt as your **first interaction** with Claude Code:

**Step 1:** Copy the `.claude/commands/` directory from this repo:
```bash
# Clone this repo temporarily to get the commands
git clone https://github.com/YOUR_USERNAME/my-claude-setup.git /tmp/claude-setup
cp -r /tmp/claude-setup/.claude /path/to/your/project/
```

**Step 2:** Open your project in Claude Code and paste this initialization prompt:

```
Initialize the project scaffolding for autonomous Claude Code development. Execute these steps systematically:

1. Create directory structure:
   mkdir -p .claude/commands .claude/skills trees tests

2. Create features.json tracking every atomic requirement with passes: false
   - Include: id, name, description, status, passes, testCommand for each feature
   - Base features on project requirements below

3. Write init.sh to bootstrap the dev environment:
   - Install dependencies (npm/pip/poetry/etc.)
   - Start services (dev server, database, etc.)
   - Set up environment variables
   - Make executable: chmod +x init.sh

4. Create HANDOFF.md summarizing current architectural decisions:
   - Current State: "Project initialized"
   - Architectural Decisions: Tech stack, directory structure, testing approach
   - Next Step: First feature to implement

5. Initialize git environment:
   - git init (if not already initialized)
   - Create .gitignore: node_modules, .env, *.log, .claude/plans, __pycache__, etc.
   - Initial commit: "chore: Initialize Claude Code project structure"

6. Create CLAUDE.md with operating protocols:
   - Sync Flow protocol
   - Engineering standards (test coverage, code style, etc.)
   - Shift-End protocol
   - Critical commands specific to this project

Project Context:
- Description: [YOUR PROJECT DESCRIPTION - e.g., "Task management API with user authentication"]
- Tech Stack: [YOUR TECH STACK - e.g., "Node.js + Express + PostgreSQL + React"]
- Initial Features: [KEY FEATURES - e.g., "User auth, Task CRUD, Tags, Search"]

After initialization, commit all files and confirm setup complete.
```

**What Claude will create:**
- **Directory structure**: `.claude/commands/`, `.claude/skills/`, `trees/`, `tests/`
- **features.json**: Feature tracking with test commands
- **init.sh**: Environment bootstrap script (executable)
- **HANDOFF.md**: Architectural state documentation
- **CLAUDE.md**: Project-specific operating protocols
- **.gitignore**: Tech stack-appropriate ignore patterns
- **Git repo**: Initialized with initial commit

---

### Customize for Your Project

After setup (via either option), customize these files:

**features.json** - Define your features:
```json
{
  "features": [
    {
      "id": "f001",
      "name": "User Authentication",
      "description": "Implement login/signup with JWT",
      "status": "pending",
      "passes": false,
      "testCommand": "npm test -- auth.test.js"
    }
  ]
}
```

**init.sh** - Add your environment setup:
```bash
#!/bin/bash
# Add your project initialization commands
npm install
# Start dev server, database, etc.
```

**CLAUDE.md** - Adapt to your project's needs:
- Update tech stack references
- Specify test commands
- Define engineering standards
- Add project-specific protocols

### Start Your First Session

```bash
# In Claude Code, run:
/sync
```

This will:
- Read your project state from `features.json` and `HANDOFF.md`
- Run `init.sh` to set up the environment
- Check Git status for uncommitted work
- Present a comprehensive summary
- Ask what feature to implement next

## File Structure

```
.
├── .claude/
│   ├── commands/
│   │   ├── sync.md          # Project state synchronization command
│   │   ├── commit.md        # Semantic commit workflow
│   │   └── add.md           # Custom command generator
│   └── settings.local.json  # MCP server configuration
├── .mcp.json                # MCP server definitions
├── CLAUDE.md                # Project-specific AI instructions
├── features.json            # Feature tracking checklist
├── HANDOFF.md               # Session context handoff
├── init.sh                  # Environment initialization
├── tests/                   # Test files directory
└── trees/                   # Git worktrees directory
```

### File Descriptions

| File | Purpose |
|------|---------|
| **CLAUDE.md** | Core instructions defining operating protocols, engineering standards, and workflows that Claude follows |
| **features.json** | JSON checklist of features to implement, with status tracking and test commands |
| **HANDOFF.md** | Narrative context from the previous session: what was achieved, blockers, and next steps |
| **init.sh** | Script to initialize the development environment (install deps, start services, etc.) |
| **.mcp.json** | MCP server configuration for documentation access |
| **tests/** | Directory for test files referenced in feature test commands |
| **trees/** | Directory for Git worktrees (for parallel feature development) |

## Custom Commands

### `/sync` - Project State Synchronization

Synchronizes the project state at the start of each session.

**Usage:**
```bash
/sync
```

**What it does:**
1. Reads `CLAUDE.md`, `features.json`, and `HANDOFF.md`
2. Executes `init.sh` to verify environment setup
3. Runs `git status` and `git log` to check for changes
4. Cross-references Git history with documentation
5. Presents a comprehensive state summary
6. Asks what feature to implement next

**Example with arguments:**
```bash
/sync implement user profile page
```
This syncs state and immediately starts planning the specified feature.

**State Summary Output:**
```
PROJECT STATE SYNCHRONIZATION
==============================

CONFIGURATION:
- CLAUDE.md: Found
- features.json: 5 features (2 complete, 1 in progress, 2 pending)
- HANDOFF.md: Found

ENVIRONMENT:
- Init script: Executed successfully
- Dependencies: Installed (npm)
- Services: Running (dev server on port 3000)

GIT STATUS:
- Branch: feature/user-auth
- Uncommitted changes: 2 files modified
- Recent commits: feat(auth): Add JWT token validation (2 hours ago)

FEATURES:
- Total: 5
- Completed: 2
- In Progress: 1 (User Authentication)
- Pending: 2

NEXT: Ready for feature implementation.
```

### `/commit` - Semantic Commit Workflow

Reviews changes and creates a semantic commit with a meaningful message.

**Usage:**
```bash
/commit
```

**What it does:**
1. Shows `git status` and diff summary
2. Displays recent commits for style reference
3. Suggests a semantic commit message
4. Asks for confirmation before committing

**Optional message context:**
```bash
/commit Added password reset feature
```

**Commit Message Format:**
- Follows [Conventional Commits](https://www.conventionalcommits.org/)
- Format: `type(scope): description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`
- Imperative mood: "Add feature" not "Added feature"
- Under 72 characters

### `/add` - Custom Command Generator

Creates new custom slash commands with best practices.

**Usage:**
```bash
/add <command-name> <description>
```

**Example:**
```bash
/add review Code review checklist command
```

**What it does:**
1. Parses the command name and description
2. Researches best practices for similar commands
3. Generates a well-structured command file
4. Saves to `.claude/commands/<command-name>.md`
5. Explains usage and incorporated best practices

**Generated Command Structure:**
- Clear purpose and context setting
- Structured instructions with numbered steps
- Proper `$ARGUMENTS` handling
- Output format specification
- Edge case handling

## Workflows

### Starting a New Session

```bash
# 1. Open your project in Claude Code
# 2. Run the sync command
/sync

# Claude will:
# - Load project state
# - Check Git status
# - Show what's been done and what's pending
# - Ask what to work on next

# 3. Specify your feature
"Implement user profile page with avatar upload"

# Claude will:
# - Plan the implementation
# - Write the code
# - Run tests
# - Update features.json
# - Commit changes
```

### Implementing a Feature

The setup follows the **Sync Flow** protocol defined in `CLAUDE.md`:

1. **State Discovery**: Load context from files and Git
2. **Task Execution**: Work on one atomic feature from `features.json`
3. **Verification**: Run test command, mark as `passes: true` only if tests pass
4. **Commit**: Create atomic commit with semantic message
5. **Handoff**: Update `HANDOFF.md` with current state and next steps

### Ending a Session (Shift-End Protocol)

Before you end a session, Claude should:

1. **Update `features.json`**: Mark current feature as complete with `passes: true`
2. **Update `HANDOFF.md`**:
   - Current State: What was achieved this session
   - Technical Debt/Blockers: Issues to address
   - Next Step: Specific task for next session
3. **Commit**: Final commit linking to the feature ID

This ensures the next session starts with complete context.

### Parallel Feature Development

For complex features or parallel work:

```bash
# Create a Git worktree for isolation
git worktree add trees/feature-name -b feature-name

# Work in the worktree
cd trees/feature-name
/sync

# When done, merge back to main
git worktree remove feature-name
```

## Configuration

### Adapting to Your Tech Stack

**Update `CLAUDE.md`** with your specific commands:

```markdown
## 4. Critical Commands
- **Initialization**: `docker-compose up -d`
- **Checklist Status**: `cat features.json`
- **Context Refresh**: `/sync`
- **Primary Test Suite**: `pytest tests/`
- **Linting**: `npm run lint`
```

### Adding MCP Servers

Edit `.mcp.json` to add more servers:

```json
{
  "mcpServers": {
    "your-docs": {
      "type": "sse",
      "url": "https://gitmcp.io/your-org/your-repo"
    }
  }
}
```

Enable in `.claude/settings.local.json`:

```json
{
  "enabledMcpjsonServers": ["your-docs"],
  "enableAllProjectMcpServers": true
}
```

### Customizing Engineering Standards

Modify the **Engineering Standards** section in `CLAUDE.md`:

```markdown
## 2. Engineering Standards
- **Test Coverage**: Maintain >80% coverage
- **Code Style**: Run `npm run lint` before commits
- **Documentation**: Update README for new features
- **Security**: Run `npm audit` before marking features complete
```

## Best Practices

### Feature Definition

Write clear, testable features in `features.json`:

```json
{
  "id": "f003",
  "name": "API Rate Limiting",
  "description": "Implement rate limiting with Redis: 100 req/min per user",
  "status": "pending",
  "passes": false,
  "testCommand": "npm test -- ratelimit.test.js",
  "acceptanceCriteria": [
    "Returns 429 after 100 requests in 1 minute",
    "Rate limit resets after 60 seconds",
    "Different users have separate limits"
  ]
}
```

### HANDOFF.md Template

Structure your handoff notes consistently:

```markdown
# Session Handoff - [Date]

## Current State
Completed user authentication feature:
- JWT token generation and validation
- Login/signup endpoints
- Password hashing with bcrypt
- Tests passing (14/14)

## Technical Debt/Blockers
- Need to add refresh token rotation
- Email verification not yet implemented

## Next Step
Implement refresh token rotation (feature f002):
1. Add refresh token to database schema
2. Create token rotation endpoint
3. Update client to use refresh flow
```

### Atomic Commits

Keep commits small and focused:

```bash
# Good
feat(auth): Add JWT token generation
feat(auth): Add password hashing
feat(auth): Add login endpoint

# Not ideal
feat(auth): Complete entire authentication system
```

### Git Worktrees for Complex Features

Use worktrees when:
- Feature requires major refactoring
- Working on multiple features in parallel
- Testing different architectural approaches

```bash
git worktree add trees/refactor-db -b refactor-db
cd trees/refactor-db
# Work in isolation
```

## Philosophy

This setup is built around three core principles:

### 1. Persistent Memory
AI agents lose context between sessions. This setup preserves:
- **What was done**: Git history and `features.json` status
- **Why it was done**: Commit messages and `HANDOFF.md` notes
- **What's next**: Explicit next steps in `HANDOFF.md`

### 2. Atomic Workflow
Work on one feature at a time:
- Clear scope in `features.json`
- Verify with tests before marking complete
- Commit immediately after verification
- No context-switching mid-feature

### 3. Git as Source of Truth
Git history provides crucial context:
- Recent changes inform new implementations
- Uncommitted work indicates interrupted sessions
- Commit patterns reveal architectural evolution

The `/sync` command cross-references Git with documentation to catch inconsistencies.

## Examples

### Example Session Flow

```
You: /sync

Claude: [Reads files, checks Git, runs init.sh]

PROJECT STATE SYNCHRONIZATION
==============================
Configuration: All files found
Environment: Dev server running on :3000
Git: On main, 2 commits since last handoff
Features: 3 total (1 complete, 2 pending)

Ready for development. What would you like to implement?

You: Add password reset feature

Claude: [Plans implementation]
I'll implement password reset with:
1. Password reset token generation
2. Email sending with reset link
3. Token validation and password update
4. Tests for the flow

Proceeding with implementation...

[Writes code, runs tests]

✓ Tests passing (4/4)
✓ Updated features.json (f002: passes = true)
✓ Committed: feat(auth): Add password reset flow

Ready to update HANDOFF.md for session end.

You: /commit

Claude: [Shows changes and creates commit]

Done! Session complete. Next time run /sync to continue.
```

### Example features.json

```json
{
  "features": [
    {
      "id": "f001",
      "name": "User Authentication",
      "description": "JWT-based authentication with login/signup",
      "status": "completed",
      "passes": true,
      "testCommand": "npm test -- auth.test.js",
      "completedAt": "2025-01-05T14:30:00Z",
      "commit": "a3f9d2c"
    },
    {
      "id": "f002",
      "name": "Password Reset",
      "description": "Email-based password reset flow",
      "status": "completed",
      "passes": true,
      "testCommand": "npm test -- reset.test.js",
      "completedAt": "2025-01-05T16:45:00Z",
      "commit": "b8e4a1f"
    },
    {
      "id": "f003",
      "name": "User Profile",
      "description": "Profile page with avatar upload",
      "status": "in_progress",
      "passes": false,
      "testCommand": "npm test -- profile.test.js"
    },
    {
      "id": "f004",
      "name": "Email Notifications",
      "description": "Send email on important account events",
      "status": "pending",
      "passes": false,
      "testCommand": "npm test -- notifications.test.js"
    }
  ]
}
```

## Troubleshooting

### "/sync command not found"

The commands are defined in `.claude/commands/`. Ensure:
1. Files exist: `ls .claude/commands/`
2. Claude Code recognizes them (restart if needed)
3. Files have `.md` extension

### "Git history out of sync with HANDOFF.md"

Run `/sync` - it will detect the discrepancy and show:
- Commits not documented in HANDOFF.md
- Suggested updates to bring documentation current

### "Tests failing but feature marked complete"

This violates the No-Clutter Rule. The feature should only be marked `passes: true` after tests pass. To fix:
1. Update `features.json`: set `passes: false`
2. Fix the failing tests
3. Re-run the test command
4. Only then mark as complete

### "Multiple features in progress"

The Atomic Workflow requires one feature at a time. To fix:
1. Complete or pause current feature
2. Update `features.json` to reflect accurate status
3. Use Git worktrees if you need parallel work

## Contributing

Have ideas to improve this setup? Contributions welcome!

### Adding New Commands

```bash
/add your-command-name Description of what it does
```

Or manually:
1. Create `.claude/commands/your-command.md`
2. Follow the structure in existing commands
3. Test it with `/your-command`

### Improving Workflows

Found a better way to structure features or handoffs? Open an issue or PR with:
- Description of the improvement
- Example of the new format
- Why it's better than current approach

## License

MIT License - feel free to adapt this setup for your projects.

---

**Built for autonomous AI development with Claude Code**

For questions or issues, open a GitHub issue or discussion.
