# Toolkit Setup and Restoration Guide

This repository records the intended MCP toolkit for ORBIT. MCP availability is environment- and account-specific; cloning this repository does not install or authenticate integrations automatically.

## Principles

1. Inspect the active Manus MCP registry and existing connectors before adding anything.
2. Reuse native Manus integrations where they already satisfy the use case.
3. Verify provider identity, official endpoint/installation instructions, maintenance status, auth model, compatibility, permissions, and cost before configuring a new MCP.
4. Prefer minimal scope and read-only validation.
5. Never put API keys, tokens, passwords, private keys, cookies, service-role credentials, or raw secret-bearing connector exports in Git.
6. Treat “listed”, “configured”, “authenticated”, and “validated” as distinct states; update [`MCP_TOOLKIT.md`](MCP_TOOLKIT.md) with evidence.

## Current-session restore checklist

1. Open this repository and read `README.md`, `INITIAL_PLAN.md`, `MCP_TOOLKIT.md`, and the most recent entries in `EXECUTION_LOG.md`.
2. Inspect `manus-config connector list` and the active session MCP registry. Preserve working connectors and do not assume the previous session's authentication persists.
3. If connector changes are required, use the approved Manus connector flow and provider's official documentation. Complete OAuth or credential steps through the proper user-facing authorization card. Do not commit local connector config or secrets.
4. Follow the pending validation matrix in `MCP_TOOLKIT.md` using harmless operations only.
5. Record versions only when they are observable from official/server metadata; otherwise mark them unknown.
6. Commit only redacted documentation and non-secret project artifacts to this private repository.

## Environment-specific notes

- The active Manus session may supply Context7, Playwright, Supabase, Vercel, and other integrations as managed servers. These should be inspected before attempting a duplicate connector.
- Native file tools can replace a dedicated filesystem MCP for the current task.
- Native platform search can replace Exa for generic web discovery, but it should not be mislabeled as Exa.
- Do not run destructive Supabase or Vercel actions as part of toolkit validation.
- GitHub CLI authentication must remain within the existing authorized configuration; do not run `gh auth login` or alter global Git/GitHub settings.

## Updating this guide

When a new integration is added, document its official source, exact installation/connector method, observable version, config location (without credential values), required permissions, authentication state, tools exposed, test performed, date, and limitations. Include restoration steps that do not depend on a copied secret.
