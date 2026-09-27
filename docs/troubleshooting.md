# Troubleshooting

## Google sign-in does not complete

Retry in a fresh browser tab and allow redirects to `ekord.app`. Signing out and
back in can re-establish the browser session.

## No paired device

Run `ekord`. Verify the automatically opened pairing request while signed in to
the intended Ekord account, or enter its 6-character code from Connections.

## Agent offline

Start the Agent and confirm it can reach the network. A previously paired Agent
reconnects using its stored device credential.

## Pairing browser did not open

The Agent also prints the full pairing page URL. Open that URL in a browser
signed in to the intended Ekord account, or enter its 6-character code from
Connections. Codes are valid for 15 minutes.

## Expired pairing request

Pairing codes are valid for 15 minutes and single-use. Start `ekord` again to
create a fresh request.

## Wrong account or revoked credential

Run `ekord --pair` and approve the new request from the correct account. A
revoked credential cannot reconnect and must be paired again.

## MCP authorization failed or expired

Re-authorize the Ekord MCP server from the AI client's MCP settings. Do not
paste tokens or OAuth secrets manually.

## Privileged mode locked

This is expected by default. Only when elevated work is intentional, ask the AI
to temporarily unlock the `security` guard.

## Read/write denied

The local OS user lacks access. Choose a path that user can access or
intentionally change local OS permissions. Unlocking Ekord does not create OS
privileges the account does not have.

## Path not found

Use `inspect` with stat/list to verify the path before retrying a mutation.

## Timeout or a command that keeps running

Use `exec` for commands expected to finish. Use `process_start` /
`process_read` / `process_control` for long-running or input-driven work.

## Truncated output

Results are bounded. Read a smaller range, continue from the reported
offset/cursor, or increase the requested bound within the tool limits.

## Unknown process ID

Process handles live in Agent memory. If the Agent restarted or the process
expired, start the process again.

## TTY-only program does not behave normally

The current process tools use pipes and do not provide a PTY. Prefer a
non-interactive command mode when the program offers one.
