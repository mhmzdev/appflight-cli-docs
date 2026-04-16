# whoami

Prints the identity of the currently authenticated user.

```bash
appflight_cli whoami
```

## Output

```
uid:         abc123xyz
email:       you@example.com
auth source: apiKey
```

## When to use

- After `login` to confirm the key was saved correctly
- In CI logs to verify the right API key is active
- When debugging authentication issues

> **Note:** `whoami` reads credentials from `APPFLIGHT_API_KEY` (env var) first, then `~/.appflight/credentials.json`.
