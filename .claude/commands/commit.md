---
allowed-tools: Bash(git status:*), Bash(git diff:*), Bash(git add:*), Bash(git commit:*), Bash(git log:*), Bash(git branch:*)
argument-hint: [optional-message]
description: Review git status and create a semantic commit
---

## Context

Current branch: !`git branch --show-current`

### Git Status
!`git status`

### Staged Changes
!`git diff --cached --stat`

### Unstaged Changes Summary
!`git diff --stat`

### Recent Commits (for style reference)
!`git log --oneline -5`

## Task

Based on the context above:

1. **Review** the current git status and changes
2. **Stage** relevant files if needed (ask user for confirmation before staging)
3. **Create** a commit with a meaningful message

### Commit Message Guidelines

- Follow conventional commits format: `type(scope): description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, `build`, `ci`
- Keep the subject line under 72 characters
- Use imperative mood ("Add feature" not "Added feature")

### User-Provided Context
$ARGUMENTS

If no message context is provided, analyze the changes and suggest an appropriate commit message. Always confirm with the user before committing.
