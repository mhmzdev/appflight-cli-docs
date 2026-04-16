# Environment Variables

Control which AppFlight server the CLI talks to and how it authenticates. Primary config mechanism for CI/CD.

## Reference

| Variable | Description | Default |
|----------|-------------|---------|
| `APPFLIGHT_API_KEY` | API key. Takes precedence over `~/.appflight/credentials.json`. | — |
| `APPFLIGHT_ENV` | Target environment: `local`, `stage`, or `prod`. | `stage` |

## APPFLIGHT_API_KEY

Used on CI/CD build servers where running `login` interactively isn't possible.

```bash
export APPFLIGHT_API_KEY=appflight_xxxxxxxxxxxx
appflight_cli upload --flavor stage
```

Generate the key in **AppFlight mobile app → Settings → API Keys**, then add it as a secret in your CI platform.

## APPFLIGHT_ENV

Controls which backend the CLI connects to.

**Local emulator:**

```bash
export APPFLIGHT_ENV=local
# Points at: http://localhost:5001/app-flight-stage/us-central1/api/v1
```

Start the emulator first: `cd functions && npm run serve`

**Stage (default):**

```bash
export APPFLIGHT_ENV=stage
# Or just don't set it — stage is the default
```

**Production:**

```bash
export APPFLIGHT_ENV=prod
```

You can also override for a single command with `--env`:

```bash
appflight_cli upload --flavor prod --env prod
```
