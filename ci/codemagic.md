# Codemagic

## Setup

1. **Generate an API key** — AppFlight mobile app → Settings → API Keys → **+** — label it `Codemagic`
2. **Add environment variable** — Codemagic → Teams → Environment variables → add `APPFLIGHT_API_KEY` as secret
3. **Commit `appflight.json`** to your repository

## codemagic.yaml

```yaml
workflows:
  android-release:
    name: Android Release
    environment:
      vars:
        APPFLIGHT_API_KEY: $APPFLIGHT_API_KEY

    scripts:
      - name: Install AppFlight CLI
        script: dart pub global activate appflight_cli

      - name: Build APK
        script: flutter build apk --flavor stage --release

      - name: Upload to AppFlight
        script: appflight_cli upload --flavor stage --ci

    artifacts:
      - build/app/outputs/flutter-apk/*.apk
```

## Multi-flavor

```yaml
      - name: Build and upload stage
        script: |
          flutter build apk --flavor stage --release
          appflight_cli upload --flavor stage --ci

      - name: Build and upload qa
        script: |
          flutter build apk --flavor qa --release
          appflight_cli upload --flavor qa --ci
```
