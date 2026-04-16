# GitHub Actions

## Setup

1. **Generate an API key** — AppFlight mobile app → Settings → API Keys → **+** — label it `GitHub Actions`
2. **Add secret** — GitHub repo → Settings → Secrets and variables → Actions → New repository secret → `APPFLIGHT_API_KEY`
3. **Commit `appflight.json`** to your repository (run `appflight_cli init` locally first)

## Workflow

Create `.github/workflows/appflight.yml`:

```yaml
name: Upload to AppFlight

on:
  push:
    branches: [main]

jobs:
  upload:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Flutter
        uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.x'

      - name: Set up Dart
        uses: dart-lang/setup-dart@v1

      - name: Install AppFlight CLI
        run: dart pub global activate appflight_cli

      - name: Build APK
        run: flutter build apk --flavor stage --release

      - name: Upload to AppFlight
        env:
          APPFLIGHT_API_KEY: ${{ secrets.APPFLIGHT_API_KEY }}
        run: appflight_cli upload --flavor stage --ci
```

## Multi-flavor

Repeat the build and upload steps per flavor:

```yaml
      - name: Build stage
        run: flutter build apk --flavor stage --release
      - name: Upload stage
        env:
          APPFLIGHT_API_KEY: ${{ secrets.APPFLIGHT_API_KEY }}
        run: appflight_cli upload --flavor stage --ci

      - name: Build qa
        run: flutter build apk --flavor qa --release
      - name: Upload qa
        env:
          APPFLIGHT_API_KEY: ${{ secrets.APPFLIGHT_API_KEY }}
        run: appflight_cli upload --flavor qa --ci
```
