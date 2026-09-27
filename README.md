# Ekord

**Ultra-light direct AI execution for your machine.**

Ekord connects an AI client to a computer you control through one public MCP
endpoint and one outbound Agent connection. The Agent dials out, so your machine
does not need an inbound port, NAT rule, or public listener.

```text
AI / MCP client
      |
      | HTTPS MCP + OAuth
      v
Ekord service
      |
      | persistent outbound device connection
      v
Ekord Agent  ->  your operating system
```

## Install

macOS arm64:

```sh
curl -fsSL https://ekord.app/install | sh
ekord
```

Then:

1. Sign in to your Ekord account.
2. Start the Agent; it opens the pairing page. Verify the matching device and
   approve it once.
3. Add `https://ekord.app/mcp` as a remote MCP server in a client that supports
   remote MCP with OAuth.
4. Complete the OAuth prompt with the same account.

After pairing, the Agent reuses its revocable device credential and reconnects
without pairing again.

## Tools

The MCP surface stays intentionally small:

- `inspect` — read-only read/list/stat/search, up to 16 targets per call
- `apply` — deterministic file changes (write/create/append/replace/move/delete/mkdir)
- `exec` — one bounded shell command expected to finish
- `process_start`, `process_read`, `process_control` — long-running or input-driven work
- `status` — your connection/version/privileged/telemetry state
- `security` — soft privileged-guard lock/unlock
- `desktop_inspect`, `desktop_act`, `desktop_capture` — semantic desktop access

Tool results are intentionally bounded. If output is truncated, request a smaller
range or continue from an offset/cursor.

## Security posture

- The Agent runs as your local operating-system user. The workspace root is a
  path base, not a sandbox.
- Ekord starts with privileged mode **LOCKED** as best-effort mistake prevention.
  It is not containment for hostile shell commands.
- Tool payloads are relayed to complete a request and are not used as a durable
  project-history store.
- Telemetry is disabled unless you explicitly enable it.

See [`SECURITY.md`](./SECURITY.md) and [`docs/security.md`](./docs/security.md).

## Documentation

- [Quickstart](./docs/quickstart.md)
- [Connect ChatGPT](./docs/chatgpt.md)
- [Agent](./docs/agent.md)
- [Tools](./docs/tools.md)
- [Security](./docs/security.md)
- [Privacy](./docs/privacy.md)
- [Troubleshooting](./docs/troubleshooting.md)

## Changes

See [`CHANGELOG.md`](./CHANGELOG.md).

## Repository

Official public repository: <https://github.com/oxcandy-lgtm/Ekord>. It is the
production release and public distribution source for Ekord. Report security
issues privately as described in [`SECURITY.md`](./SECURITY.md).
