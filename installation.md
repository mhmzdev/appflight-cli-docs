# Installation

## Prerequisites

The CLI requires Dart SDK `>=3.0.0`. If you have Flutter installed, you already have Dart.

```bash
dart --version
```

## Install via pub.dev

```bash
dart pub global activate appflight_cli
```

> **Note:** If `appflight_cli` is not found after installation, add the Dart pub cache bin to your PATH:
>
> ```bash
> # Add to ~/.zshrc or ~/.bashrc
> export PATH="$PATH:$HOME/.pub-cache/bin"
> ```

## Install from source

```bash
git clone https://github.com/mhmzdev/appflight_cli.git
cd appflight_cli
dart pub global activate --source path .
```

Re-run the same command after pulling updates.

## Verify

```bash
appflight_cli --help
```

## Uninstall

```bash
dart pub global deactivate appflight_cli
```
