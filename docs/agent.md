# Agent

The Agent is a small outbound-only process that runs on your machine. Supported
platform: **macOS arm64**.

## Install and start

```sh
curl -fsSL https://ekord.app/install | sh
ekord
```

Run `ekord` from the directory you want as the workspace root, or pass
`--root DIR`.

## First pairing

On first start the Agent creates a one-time pairing request with a 6-character
code valid for 15 minutes and opens the pairing page automatically. You can also
enter the code from Connections. Verify the matching device while signed in to
your Ekord account.

## Credential persistence and reconnect

The Agent stores a revocable device credential under `~/.ekord/`. On later
starts it reconnects with that credential and returns to `ready` without pairing
again.

## Force re-pair

Run `ekord --pair` when you intentionally need a new pairing. Removing the
stored credential also forces a new pairing ceremony.

## Status and version

The Agent reports `paired`, `connecting`, `ready`, and `error` states.
`ekord --version` prints the installed version.

## Workspace root

Relative paths are resolved against the workspace root. Absolute paths are used
as-is. The workspace root is **not** a filesystem sandbox. The Agent runs with
the permissions of your local operating-system user.

## Stop

Stop the foreground Agent with `Ctrl-C`. While the Agent is stopped, remote
machine execution is unavailable.
