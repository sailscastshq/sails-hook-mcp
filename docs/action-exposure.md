# Action exposure requirements

Status: design guidance; not implemented in the 0.0.0 placeholder.

## Context

On October 26, 2026, navneet.dev (@navneetsuman_) asked whether existing
Sails actions would automatically become tools or be selected explicitly.
He requested an explicit allowlist before agents could access write endpoints.
Kelvin acknowledged this feedback while shaping the official sails-hook-mcp.

## Required behavior

- Default deny. Installing the hook or adding a configuration file must not
  automatically expose every Sails action, route, blueprint, helper, or model.
- Discover and invoke only explicitly allowlisted actions. Enforce the same
  selection at tool listing and execution; knowing a hidden action name must
  not make it callable.
- Require explicit opt-in for each write action. Do not infer permission to
  mutate from a tool name, HTTP method, generated schema, or client hint.
- Preserve the application's server-side authentication, Sails policies,
  input validation, authorization, and tenant/resource access checks for every
  invocation. An allowlist selects tools; it does not grant access to data.
- Reject unknown actions and invalid exposure configuration without widening
  access. Define configuration syntax and error behavior before implementation.
- Keep the one-file developer experience while making the exposure boundary
  visible and reviewable. Document precisely what developers choose to expose.

## Acceptance criteria for implementation

- With no allowlist, tool discovery is empty and direct calls are rejected.
- An unlisted action remains unavailable even when invoked by its exact name.
- An explicitly selected read action does not enable neighboring write actions.
- A write action remains unavailable until explicitly opted in.
- Unauthenticated, unauthorized, cross-tenant, and invalid-input calls fail
  under the application's existing rules, including for allowlisted actions.
- Adding a new Sails action does not change the MCP surface until the developer
  explicitly selects it.

Transport, credentials, configuration shape, and execution integration remain
design work. Do not claim these requirements are enforced by the placeholder.
