# Security

## Execution boundary

The Agent runs as your local operating-system user and can do what that user can
do: read/write accessible files and run commands. The workspace root is a path
base, not a sandbox.

## Privileged soft guard

Ekord starts with privileged mode **LOCKED**. While locked, the service applies
best-effort checks for obvious direct sudo/root requests and common root/sudo
configuration paths before forwarding them to the Agent.

If privileged work is explicitly intended, ask the AI to use the `security` tool
to unlock it for a short period. Unlocks are account-scoped, expire after at most
30 minutes, live only in service memory, and return to locked after a restart.
The `status` tool reports the current state.

**The privileged lock is best-effort mistake prevention, not containment for
hostile shell commands.** Do not rely on it as a security sandbox. The local OS
account and its permissions are the final boundary.

## Connection direction

The Agent initiates an outbound connection to Ekord. Your machine does not need
an inbound port, NAT rule, or public listener for Ekord.

## Service-side data

Ekord stores the account/device/OAuth records needed to authenticate and route
requests. Tool payloads pass through the service to complete the request but are
not durably stored as project history. See [Privacy](./privacy.md).

## Device credentials

Each paired device has its own revocable credential. After server-side
revocation, that Agent must pair again.

## Protections

OAuth authorization uses PKCE, state and redirect binding, and short-lived
single-use authorization codes. Tool requests and results are bounded, duplicate
and retry handling preserves the intended execution identity, and reviewer
responses are kept at the public privacy boundary. Agent updates are
signature-verified before installation.

By default, Ekord does not retain a durable project or tool-history payload
store. Account, device and authorization records needed to operate the service
are retained as described in [Privacy](./privacy.md).

## Stopping access

Stopping the Agent immediately removes remote execution availability from that
machine. Revoking its credential prevents that credential reconnecting.

## Reporting a vulnerability

See [`../SECURITY.md`](../SECURITY.md).
