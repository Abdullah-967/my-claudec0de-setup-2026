# Documentation Index

> **Protocol:** Before starting any task, find your entry point below. Read ONLY the matched file(s). If no match, work from codebase directly. If you find info that should be indexed here but isn't, add a row.

## Route by File Path

| You're editing... | Read |
|-------------------|------|
| `[path/to/db/migrations/]` | [database.md](database.md) |
| `[path/to/api/]` | [api.md](api.md) |
| [add your source paths] | [doc-name.md] |

## Route by Intent

### Adding something new

| I want to... | Read |
|--------------|------|
| Add a new API endpoint | [api.md](api.md) + [database.md](database.md) |
| Add a new DB table | [database.md](database.md) |
| Understand project structure | [architecture.md](architecture.md) |

### Debugging

| The bug is in... | Read |
|------------------|------|
| Auth / permissions | [database.md](database.md) |
| API errors (4xx/5xx) | [api.md](api.md) |

### Deploying

| I need to... | Read |
|--------------|------|
| Deploy or update env vars | [deployment.md](deployment.md) |

## Combos

Multi-domain tasks that always need more than one doc:

| Task | Read |
|------|------|
| New authenticated endpoint | [api.md](api.md) + [database.md](database.md) |

## No Match?

Work directly from the codebase. Use grep/glob. Don't load docs speculatively.
