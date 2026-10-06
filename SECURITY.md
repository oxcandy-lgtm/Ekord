# Security Policy

## Reporting a vulnerability

Please report suspected vulnerabilities privately through this repository's
GitHub **Security** tab using **Report a vulnerability** (private vulnerability
reporting). Do not open a public issue for a security problem.

Include, when possible:

- a short description and impact;
- affected component (MCP endpoint, OAuth flow, pairing, Agent, desktop tools);
- reproduction steps or a minimal proof of concept;
- affected version or date observed.

We will acknowledge a report and follow up with next steps. Please give us a
reasonable window to investigate and ship a fix before public disclosure.

## Scope

Relevant areas include, but are not limited to:

- authentication, OAuth, session and pairing flows;
- device credential issuance, revocation and reconnect;
- authorization between an AI client and a paired machine;
- the MCP tool boundary and bounded-result behavior;
- the Agent's outbound connection and local execution boundary.

## Execution boundary

The Ekord Agent runs as the local operating-system user and can do what that
user can do. The workspace root is a path base, not a sandbox, and the
privileged soft guard is best-effort mistake prevention rather than containment
for hostile commands. The local OS account and its permissions are the final
security boundary.

## Protections

Ekord uses OAuth authorization protections including PKCE, state and redirect
binding, and short-lived single-use authorization codes. Paired devices use
separate revocable credentials, and the Agent connects outbound to the service.
Tool requests and results are bounded, duplicate and retry handling preserves
the intended execution identity, and reviewer responses are kept at the public
privacy boundary. Agent updates are signature-verified before installation.

By default, Ekord does not retain a durable project or tool-history payload
store. Account, device and authorization records needed to operate the service
are retained as described in the public Privacy documentation.

## Secrets

Never include real credentials, tokens, private keys or personal data in a
report. Use synthetic values.
