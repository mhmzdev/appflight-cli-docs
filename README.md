# AppFlight CLI

Upload Android APKs to AppFlight directly from your terminal or CI pipeline — no phone required.

```bash
appflight upload --flavor stage
```

## Links

| | |
|---|---|
| 🌐 **Landing page** | https://app-flight.com |
| 📖 **Documentation** | https://docs.page/mhmzdev/appflight-cli-docs |

## Quick Start

```bash
# Install (the package is appflight_cli; the command it installs is appflight)
dart pub global activate appflight_cli

# Create an account — verification link arrives by email
appflight signup

# Log in with that email and password; no key to copy
appflight login

# Register the app, then set up this project
appflight apps create --package com.myapp --name "My App"
appflight init --flavors stage:com.myapp.stage,prod:com.myapp

# Build and upload
flutter build apk --flavor stage --release
appflight upload --flavor stage
```

## Commands

| Command | Description |
|---------|-------------|
| `signup` | Create an AppFlight account from the terminal |
| `login` | Sign in with email and password; mints this machine's API key |
| `logout` | Revoke this machine's key and remove saved credentials |
| `whoami` | Print the currently authenticated user |
| `apps create` | Register a new app on AppFlight |
| `apps list` | List the apps on this account, with your role and APK count |
| `init` | Create `appflight.json` in your project root |
| `upload` | Upload a built APK to AppFlight |
| `keys create` | Create an API key for CI — printed once |
| `keys list` | List your API keys |
| `keys revoke` | Revoke an API key by label or prefix |
| `upgrade` | Show how to upgrade to First Class |
| `analytics` | Manage anonymous usage analytics |

## Requirements

- Dart SDK `>=3.0.0`
- An AppFlight account — `appflight signup` creates one

The mobile app is how testers receive builds. Developers only need it for things that are genuinely
phone-only: subscribing to First Class, and changing an organization member's role.

## Documentation

Full reference → [docs.page/mhmzdev/appflight-cli-docs](https://docs.page/mhmzdev/appflight-cli-docs)
