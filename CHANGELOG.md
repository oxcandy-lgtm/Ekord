# Changelog

Ekord follows semantic versioning for the service and the Agent. Dates are added
when a release is published.

## 0.3.x

- Signed Agent auto-update: the Agent verifies an Ed25519-signed stable-channel
  manifest, downloads and SHA-256-verifies the release artifact, stages and
  self-tests it, and atomically switches versions. A failed candidate never
  becomes current; the previous working version is kept for rollback. Pairing
  credentials are preserved across updates.
- Versioned install layout (`agent/releases/<version>` + a stable `agent/current`
  pointer and launcher) so updates never disturb the credential.
- Current MCP surface: `inspect`, `apply`, `exec`, `process_start`,
  `process_read`, `process_control`, `status`, `security`, `desktop_inspect`,
  `desktop_act`, `desktop_capture`.
- Browser semantic access via explicitly attached Chrome Remote Debugging
  (`desktop_inspect` / `desktop_act` with `provenance=cdp`), with bounded
  overview → targeted overview (SKIM) → act before heavier inspection.
- Persistent approved browser transport with idle per-target session detach;
  the browser WebSocket stays connected so reapproval is not repeatedly
  required.
- Agent reconnect via a revocable device credential; normal restarts do not
  require pairing again.
- Account and connection management: display name, password, email
  verification, machine rename/revoke, pairing.
- Durable control state in keyed SQLite/WAL; the hot tool-call path does not
  persist project payloads.

## 0.2.x

- First production vertical path: remote MCP over OAuth to a persistent
  outbound Agent, with `inspect` / `apply` / `exec`.
- macOS arm64 one-command install and browser-open pairing.
