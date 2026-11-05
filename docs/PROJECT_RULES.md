# Project Documentation and Progress Rules

This document governs how this repository records MCP setup and future ORBIT work.

## Progress records

- Document planned changes before performing them.
- Keep `EXECUTION_LOG.md` chronological and factual. Add evidence, not optimism.
- Record the state of work as planned, started, completed, blocked, or deferred.
- Record the exact scope of tests and their result; don't generalize a narrow check.
- Update `MCP_TOOLKIT.md` after actual installation or validation.
- For ORBIT engineering, map each feature to an acceptance criterion and note dependencies and deferred items.

## Security and authenticity

- Keep this repository private unless the user explicitly asks to publish it.
- Exclude `.env`, credential-bearing configs, tokens, cookies, private user data, and unapproved VFSTR data.
- Never describe demo or seeded records as live/institutional data.
- Do not claim AI-generated values are official or verified without evidence.

## Component inventory (for future app implementation)

The ORBIT prompt requires a root-level `COMPONENTS.md` documenting each sourced component's name, provider, source URL, license/usage conditions, installation method, dependencies, project location, modifications, and features. Before app work, inspect React Bits first, verify components' free status/licenses/dependencies, and choose an alternative provider only when React Bits is unsuitable. The component inventory has not yet been populated because no app components have been selected or installed.

## What this repository is not

It is not a proof that ORBIT is deployed or feature-complete. It does not contain live student records, credentials, or production database dumps. It does not imply an Android client exists.
