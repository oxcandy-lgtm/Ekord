# Privacy

This page describes the data the Ekord service handles. It is a product
description, not a certification or legal guarantee.

## Account and device data

Ekord stores the account identifier and login binding needed to sign you in,
plus paired device identifiers, revocable device credentials, online/last-seen
state, and OAuth clients/grants/tokens required for the MCP connection.

## Tool payloads

To execute a request, the service relays tool arguments and results between the
authenticated AI client and your paired Agent. Ekord does not use file bodies,
command text, stdout/stderr, patches, or project snapshots as a durable
project-history store.

## Optional product telemetry

Product telemetry is **disabled unless you explicitly enable it** in your
account. With telemetry disabled, Ekord does not create product-analytics
events. Strictly necessary security/service logs may still exist to operate the
service.

When enabled, Ekord records content-free operational metadata such as a
pseudonymous user identifier, tool name, success/failure, sanitized error
code/category, latency, coarse result-size bucket, truncation state, observed
MCP/client version, Agent/service version, and coarse activity/reconnect state.

## Telemetry never includes

- prompts, command text/arguments, or working-directory values
- paths, filenames/extensions, file/search/patch contents, stdout/stderr, or result bodies
- screenshots, clipboard contents, environment variables, tokens, secrets, or credentials
- raw error text when a sanitized error code/category is sufficient

## Turning telemetry off

Disabling telemetry stops new product-analytics events. It does not imply that
previously recorded telemetry is immediately erased.

## Retention

A fixed automatic deletion window for previously recorded telemetry is not yet
published. A production retention period must be published and enforced before
public telemetry launch.
