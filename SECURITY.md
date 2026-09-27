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

## Secrets

Never include real credentials, tokens, private keys or personal data in a
report. Use synthetic values.
