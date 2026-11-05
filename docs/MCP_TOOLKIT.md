# MCP Toolkit Inventory

**Last updated:** 2026-11-05, 13:00 IST  
**Record status:** Pre-installation baseline. A tool appearing in the Manus session registry is not, by itself, proof that its browser runtime, account permissions, or intended operations have been tested.

## Requested core toolkit

| Capability / requested MCP | Initial status | Evidence and safe interpretation | Next action |
|---|---|---|---|
| Context7 | Present in Manus session; tool inventory inspected | `resolve-library-id` and `query-docs` are exposed. No documentation query has yet been run. | Validate by retrieving current React docs. |
| Playwright | Present in Manus session; tool inventory inspected | Browser navigation, interaction, snapshots, screenshots, and console tools are exposed. Browser runtime is not yet verified. | Check official installation hook; install browser if supported, then open a harmless page. |
| Supabase | Present; runtime marks authenticated | MCP exposes project/schema/auth/storage-related operations, including project listing and read-only schema inspection. No project has been inspected or modified. | Verify expected tools only; do not alter a project during toolkit validation. |
| Vercel | Present in Manus session; tool inventory inspected | MCP exposes project/deployment/documentation and related tools. Account access for a specific project has not been validated. | Validate availability safely; avoid resource creation and secret reads. |
| GitHub MCP | Not listed in the session MCP registry | `gh` CLI is installed and authenticated to GitHub account `bunny0arch`. The repository-management requirement can currently be served by that CLI, but that is not a GitHub MCP. | Research the official GitHub MCP and Manus registration/auth options; avoid redundant setup if connector flow is unavailable. |
| Filesystem MCP | Not listed as a dedicated MCP | Manus `read`, `write`, and `edit` tools and sandbox file operations are available. The filesystem capability is present natively, but no Filesystem MCP is claimed. | Evaluate official MCP only if it materially improves authorized workspace access. |
| Exa MCP | Not listed in session registry | Platform web search exists; it is not Exa. | Verify official Exa MCP and auth model; install only if supported and useful. Otherwise document search as alternative. |
| Sequential Thinking MCP | Not listed in session registry | Native reasoning, agent, and workflow orchestration capabilities exist; none should be represented as this named server. | Verify official project status/compatibility; skip if redundant, abandoned, or incompatible. |

## Optional MCPs named in the guide

| MCP | Initial status | Decision rule |
|---|---|---|
| Figma | Not listed | Optional; configure only if there is an authorized Figma account and a concrete design file/use case. |
| Shadcn | Not listed | Optional; component docs and packages can be accessed through existing research tools. Add a server only if it provides a real supported advantage. |
| Memory | Not listed | Optional; prefer the repository/project documentation and existing session context unless a maintained MCP adds meaningful persistence. |

## Other Manus-provided integrations visible initially

The session registry also exposed `manus-tools`, `manus-device`, `handoff`, `manus-tasks`, `slides`, `triggers`, `trip`, `webdev-mcp`, and `workflow`. These are existing platform integrations; they are not being installed or modified as part of the initial audit. For ORBIT engineering, the directly relevant ones are browser tooling through `manus-tools`, task orchestration via `workflow`, and web application development via `webdev-mcp` if and when app implementation is requested.

## Authentication and permissions

- GitHub CLI status showed the account `bunny0arch` as active. No token values are stored in this repository.
- Supabase is marked authenticated at the integration level. No project-specific authorization or schema test is claimed yet.
- Vercel MCP is listed; no specific Vercel team/project operation has been authorized or validated.
- Any future MCP OAuth/API-key step that requires the account owner must be completed through the provider's proper authorization UI/card. Never copy secrets into GitHub.

## Validation matrix (pending)

| Test | Expected safe operation | Status |
|---|---|---|
| Context7 | Resolve React docs and retrieve current documentation | Pending |
| Exa / search | Find a public open-source React component repository; explicitly label the tool actually used | Pending |
| GitHub | Inspect a public repository read-only | Pending |
| Filesystem | Create, read, and remove a temporary file under this workspace | Pending |
| Playwright | Verify browser runtime, open a harmless test site, inspect page snapshot/console | Pending |
| Supabase | Confirm expected tools and, if appropriate, perform a harmless read-only project listing | Pending |
| Vercel | Confirm expected tools and safe account state without reading secrets or creating resources | Pending |
| Advanced reasoning | Verify whether a dedicated Sequential Thinking MCP can be made available; otherwise document the native alternative | Pending |

## Status vocabulary

- **Present in session:** server/tools appear in the active Manus MCP registry.
- **Configured:** connector setup exists and is enabled in the active environment.
- **Authenticated:** an authorization state is confirmed, without exposing credentials.
- **Validated:** at least one harmless operation using the integration completed successfully.
- **Unavailable:** no supported compatible connector/install route is available in this environment.
- **Deferred:** intentionally not configured because it is optional, redundant, unsafe, or needs user authorization.

Do not collapse these states or infer one from another.
