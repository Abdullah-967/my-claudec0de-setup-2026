# Deployment

## Environments

| Env | URL | Branch |
|-----|-----|--------|
| Production | [your-app.com] | `main` |
| Preview | [auto per PR] | any |

## Deploy

```bash
[your deploy command, e.g. git push origin main]
```

## Environment Variables

- Set in: [e.g. Vercel dashboard → Settings → Environment Variables]
- Required vars: [list them]

## After Deploy Checklist

- [ ] [e.g. Run DB migrations]
- [ ] [e.g. Verify auth redirect URLs]
- [ ] [e.g. Smoke-test critical flows]
