# API Routes

## Conventions

- [e.g. All routes live in `app/api/`. Each folder = one resource.]
- [e.g. Auth check: verify session at the top of every handler before touching DB]
- [e.g. Return `{ error }` on failure, `{ data }` on success]

## Route Map

| Method | Path | Purpose |
|--------|------|---------|
| GET | `/api/[resource]` | [what it returns] |
| POST | `/api/[resource]` | [what it creates] |

## Error Handling

- [e.g. 401 = unauthenticated, 403 = unauthorized (RLS), 404 = not found]
- [e.g. Never expose raw DB errors to the client]
