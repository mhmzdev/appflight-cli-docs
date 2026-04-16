# AppFlight CLI

Upload Android APKs to AppFlight directly from your terminal or CI pipeline — no phone required.

```bash
appflight_cli upload --flavor stage
```

## Links

| | |
|---|---|
| 🌐 **Landing page** | https://app-flight-stage.web.app |
| 📖 **Documentation** | https://docs.page/mhmzdev/appflight-cli-docs |

## Quick Start

```bash
# Install
dart pub global activate appflight_cli

# Init your project
appflight_cli init --flavors stage:com.myapp.stage,prod:com.myapp

# Login with your API key (generate in AppFlight app → Settings → API Keys)
appflight_cli login

# Build and upload
flutter build apk --flavor stage --release
appflight_cli upload --flavor stage
```

## Commands

| Command | Description |
|---------|-------------|
| `init` | Create `appflight.json` in your project root |
| `login` | Save your API key to `~/.appflight/credentials.json` |
| `upload` | Upload a built APK to AppFlight |
| `whoami` | Print the currently authenticated user |
| `logout` | Remove saved credentials from this machine |

## Requirements

- Dart SDK `>=3.0.0`
- An AppFlight account with at least one app created
- An API key from the AppFlight mobile app

## Documentation

Full reference → [docs.page/mhmzdev/appflight-cli-docs](https://docs.page/mhmzdev/appflight-cli-docs)
