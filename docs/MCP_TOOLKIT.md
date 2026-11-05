# MCP Toolkit Inventory

**Last updated:** 2026-11-05, 13:08 IST
**Status:** Source verification and browser-runtime validation complete. Connector setup is pending. A catalog entry or successful package download does not by itself prove that the integration is enabled or operational.

## Requested core toolkit

| Capability / requested MCP | Verified status | Evidence and next action |
|---|---|---|
| Context7 | Present and enabled in this task's connector catalog | Context7 tools are exposed in the session. No library-documentation query has yet been used to validate the connector. |
| Playwright | Present, runtime installed, validated | Firefox 158.0 was installed with the browser-specific command recommended by the MCP's own error. Playwright opened official provider documentation pages and `https://example.com`; the test page rendered successfully. The MCP tool list did not expose a `browser_install` operation. |
| Supabase | Present; integration reports authenticated | Supabase tools were inventoried. No project was selected or modified; project-level access remains untested. |
| Vercel | Present in the session | No particular team or project was accessed or changed. |
| GitHub | Built-in GitHub connector enabled; `gh` CLI authenticated as `bunny0arch` | Used the CLI to create and push this private repository. The GitHub MCP ensure flow selected this existing integration and did not create a separate hosted MCP. No OAuth/PAT was added to a custom server. |
| Filesystem MCP | Official package verified; connector not yet configured | Official package `@modelcontextprotocol/server-filesystem` v2.2.0 reports Node.js `>=24`; the sandbox's default Node is v22.23.4. An isolated Node 24.22.2 runtime was successfully resolved via `npx --package=node@24`. If configured, the MCP will be restricted to this repository folder only. |
| Exa MCP | Existing official catalog connector remains disabled; activation was not accepted | No retry or alternate Exa connector will be created. Use Manus platform web search when needed and label it as such, not as Exa. |
| Sequential Thinking MCP | Official package verified; connector not yet configured | Package v2.1.1 reports Node.js `>=24`, while the default runtime is v22.23.4. The isolated Node 24.22.2 runtime works. It can be added locally with thought logging disabled, if configuration succeeds. |

## Optional MCPs named in the guide

| MCP | Verified status | Decision |
|---|---|---|
| Figma | Not listed in the active session | Optional. Defer unless a Figma file and authorized account are needed for the ORBIT design workflow. |
| Shadcn | Not listed as a dedicated MCP | Optional. Current docs/search sources can retrieve component information; defer unless a concrete advantage appears. |
| Memory | Not listed as a dedicated MCP | Optional. The private GitHub repository and current session already provide project persistence; defer unless longer-term memory becomes necessary. |

## Other Manus-provided integrations visible initially

The session also exposes `manus-tools`, `manus-device`, `handoff`, `manus-tasks`, `slides`, `triggers`, `trip`, `webdev-mcp`, and `workflow`. These are existing platform integrations, not installations performed for the ORBIT application. Relevant existing capability coverage includes browser automation, file operations, and workflow orchestration.

## Permissions and secrets

The GitHub CLI is authenticated as `bunny0arch`; no credential has been copied from it into an MCP configuration or this repository. The GitHub built-in connector is enabled. The official remote GitHub MCP's read-only endpoint remains separate and may require OAuth authorization through Manus.

Exa search/fetch can run keylessly under Exa's documented free rate limit. Do not add an API key unless the user separately authorizes authenticated or usage-based access. Supabase is marked authenticated at the integration level, but no project-level access is claimed. Never place API keys, PATs, cookies, or service-role credentials in this repository.

## Validation matrix

| Test | Result |
|---|---|
| Context7 documentation lookup | Pending |
| Exa public web search | Pending activation and validation |
| GitHub repository read | `gh` CLI validated by private repository creation and push; GitHub MCP itself pending |
| Filesystem MCP restricted workspace operation | Pending connector setup |
| Playwright open and inspect page | Passed: official provider pages and `example.com` opened; test page rendered |
| Supabase operation | Not run; no project selected or modified |
| Vercel operation | Not run; no project selected or modified |
| Sequential Thinking tool availability | Pending connector setup |

## Status vocabulary

- **Present:** tools or a connector entry appear in the active Manus session/catalog.
- **Enabled:** the connector is active for the current task.
- **Authenticated:** authorization is confirmed at the stated integration level.
- **Validated:** a harmless operation completed successfully.
- **Pending:** setup or validation has not been completed.
- **Deferred:** intentionally not configured because it is optional, redundant, unsafe, or incompatible.

Do not infer one status from another.
