# MCP Toolkit Inventory

**Last updated:** 2026-11-05, 13:22 IST
**Status:** Core integrations audited; local Filesystem and Sequential Thinking MCPs installed and validated. This inventory distinguishes platform integrations from standalone MCP servers and records when an operation was intentionally not run.

## Requested core toolkit

| Capability | Verified status | Evidence, permissions, and limitation |
|---|---|---|
| Context7 | Present, enabled, and validated | Exposes `resolve-library-id` and `query-docs`. Resolved `/reactjs/react.dev` and retrieved current official React `useState` documentation. The managed server build version is not exposed. No secrets or private code were sent. |
| Playwright | Present; Firefox runtime installed; basic browser validation passed | Installed the Firefox runtime using the command recommended by the Playwright MCP error. Firefox 158.0 opened official provider documentation pages and `https://example.com`; the page rendered and a snapshot was captured. The managed MCP build version is not exposed; no full application workflow was tested. |
| Supabase | Present; integration reports authenticated; expected tools exposed | Listed 31 tools, including `list_projects`, `list_tables`, `apply_migration`, and `execute_sql`. The managed server version is not exposed. No project was selected and no database/auth/storage resource was read or changed. |
| Vercel | Present; expected tool surface exposed | Listed 246 tools, including project/deployment, runtime-log, and error-inspection operations. The managed server version is not exposed. No team/project was selected and no deployment or configuration was changed. |
| GitHub | Built-in connector enabled; authenticated `gh` CLI validated | Used the CLI to create and push this private repository and to read public `reactjs/react.dev` metadata. `manus-mcp-cli` does not expose a `github` MCP server. The GitHub MCP ensure flow resolved to the already-enabled built-in integration, so no separate remote GitHub MCP or duplicate connector was created. The built-in integration's package version is not exposed. No PAT or OAuth credential was copied into a custom connector. |
| Filesystem MCP | Created, enabled, and end-to-end validated | Official `@modelcontextprotocol/server-filesystem@2.2.0`, run under isolated Node v24.22.2. The only allowed directory is `/home/ubuntu/orbit-mcp-toolkit`. The 16-tool surface includes read/write/append/edit, search, copy/move, and directory inspection; it exposes no `delete_file` tool. A temporary file was written and read through the MCP, then removed through the shell; no test file remains. Connector UID: `d1277358-15cd-4f0b-a085-235dc5774724`. |
| Exa MCP | Existing official catalog connector remains disabled | The activation suggestion was not accepted. No retry or alternate/custom Exa connector will be created. Exa validation was not run; use Manus platform search when needed and do not label it as Exa. |
| Sequential Thinking MCP | Created, enabled, and tool-validated | Official `@modelcontextprotocol/server-sequential-thinking@2.1.1`, run under isolated Node v24.22.2, with `DISABLE_THOUGHT_LOGGING=true`. The expected tool was listed and a harmless high-level operational call succeeded. Connector UID: `37f65ca3-9057-4bcd-ac78-829ff1ef094c`. |

## Optional MCPs named in the guide

| MCP | Status and decision |
|---|---|
| Figma | Not installed. The guide makes this optional and requires compatibility with an available Figma account; no Figma account authorization was checked or requested. |
| Shadcn | No dedicated MCP installed. The guide says not to install a separate server for every component library; use Context7, provider documentation, package registries, and public repositories as appropriate. |
| Memory | Not installed. The guide says to add it only if it provides meaningful value beyond Manus memory/project context; the private GitHub repository and existing project context cover the current need. |

## Other Manus-provided integrations visible initially

The session also exposes `manus-tools`, `manus-device`, `handoff`, `manus-tasks`, `slides`, `triggers`, `trip`, `webdev-mcp`, and `workflow`. These are platform integrations rather than installations performed for the ORBIT application. They provide equivalent or complementary capabilities such as browser automation, file operations, project management, and workflow orchestration.

## Permissions and secrets

The GitHub CLI is authenticated as `bunny0arch`; no credential has been copied into an MCP configuration or committed here. Supabase reports authenticated at the integration level, but no project-level access is claimed. Vercel was not connected to a particular team or project during validation. Exa remains disabled. Never put API keys, PATs, cookies, passwords, or service-role credentials in this repository.

## Validation matrix

| Test | Result |
|---|---|
| Context7 React documentation lookup | Passed: resolved the official React documentation library ID and retrieved `useState` material |
| Exa public web search | Not run; activation was not accepted |
| GitHub public repository inspection | Passed through `gh` CLI for public `reactjs/react.dev`; not a GitHub MCP test |
| Filesystem MCP scope | Passed: allowed-directory tool returned only the toolkit repository |
| Filesystem MCP write/read round trip | Passed: temporary file written and read through MCP, then cleaned up; no test file remains |
| Playwright open and inspect page | Passed for basic navigation/snapshot: official provider pages and `example.com` opened |
| Supabase and Vercel expected tools | Passed: 31 Supabase and 246 Vercel tools listed; no project resources modified |
| Sequential Thinking tool | Passed: expected tool listed and harmless high-level call succeeded |

## Status vocabulary

- **Present:** tools or a connector entry appear in the active Manus session/catalog.
- **Enabled:** the connector is active for the current task.
- **Authenticated:** authorization is confirmed at the stated integration level.
- **Validated:** a harmless operation completed successfully.
- **Pending:** setup or validation has not been completed.
- **Deferred:** intentionally not configured because it is optional, redundant, unsafe, incompatible, or not accepted.

Do not infer one status from another.
