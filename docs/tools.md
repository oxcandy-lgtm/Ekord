# Tools

Ekord keeps a small tool catalog so the AI has fewer choices and less
schema/context overhead. Paths refer to the paired machine.

## `inspect` — read-only inspection

Read, list, stat, or search a path. It can inspect up to 16 independent targets
in one call, with bounded output and partial success when one target fails.

## `apply` — deterministic file changes

Write, create, append, literal replace, move, delete, or make a directory.
Literal replace checks the expected match count before writing; a mismatch makes
no change. Move does not overwrite an existing destination by default.

## `exec` — one command expected to finish

Run a bounded shell command and return stdout/stderr plus exit state. Use this
for work expected to terminate promptly.

## `process_start`, `process_read`, `process_control`

Use these for long-running or input-driven work. A process gets an opaque
`process_id`; read output with a cursor and control input/signals separately.
Process state is held in Agent memory, so an Agent restart can invalidate
existing process IDs. The current process transport uses pipes, not a PTY.

## `status` — your connection state

Read your service/Agent version, platform, device online state, privileged
state, telemetry state, and optional sanitized usage/error summaries.

## `security` — soft privileged guard

Lock or temporarily unlock Ekord's privileged mistake-prevention guard. The
operating-system account remains the real security boundary.

## Desktop tools

`desktop_inspect`, `desktop_act`, and `desktop_capture` provide semantic
desktop access. When Chrome Remote Debugging is explicitly enabled and approved,
browser targets are served over CDP with `provenance=cdp` and page content
treated as untrusted data. A targeted overview returns a compact SKIM (actions
and content) before heavier inspection.

## Bounded results

File and process output is intentionally bounded. If a result is truncated,
request a smaller range, continue from an offset/cursor, or split the work
instead of assuming missing output means success.
