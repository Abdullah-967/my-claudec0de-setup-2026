# Database

## Schema Overview

| Table | Purpose |
|-------|---------|
| [table_name] | [what it stores] |

## Key Relationships

- [e.g. `users` 1→N `projects`]

## Auth / RLS

- [e.g. All tables have RLS enabled. Users can only access rows where `user_id = auth.uid()`]

## Migrations

- Location: `[path/to/migrations/]`
- Run: `[migration command]`
- Always check Supabase security + performance advisors after DDL changes
