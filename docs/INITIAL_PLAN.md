# Initial Plan and Baseline Audit

**Prepared:** 2026-11-05, 13:00 IST  
**Purpose:** Create a durable record before beginning MCP installation/configuration or validation.  
**State:** Baseline documentation prepared; no MCP installation/configuration has started.

## Requested outcome

Build a reusable, secure software-development MCP toolkit for ORBIT and future projects. Inspect the current Manus environment first; reuse available integrations; install only useful, maintained, compatible capabilities; avoid duplicates; validate integrations safely; and document actual results, authentication requirements, and limitations.

## ORBIT context

The provided ORBIT brief describes a VFSTR-centered student career-intelligence and skill-development platform. It prioritizes a functional web application, evidence-backed skill profiles, career-role gap analysis, personalized learning plans, persistent progress, source-grounded AI, and security. See [`ORBIT_PROMPT_ANALYSIS.md`](ORBIT_PROMPT_ANALYSIS.md) for the complete structured summary. This MCP-toolkit task does not itself implement ORBIT.

## Baseline findings (read-only inspection)

1. The current Manus session exposes Context7, Playwright, Supabase, and Vercel MCP servers, with the tool families described in [`MCP_TOOLKIT.md`](MCP_TOOLKIT.md).
2. Playwright has browser interaction tools, but a browser runtime installation has not yet been verified. The available integration instructions call for checking/installing the browser before browser tests.
3. Supabase MCP is marked authenticated by the runtime. No project has been selected or changed.
4. Vercel MCP is present. No deployment, project, domain, or secret configuration was changed or inspected for secret values.
5. GitHub MCP is not listed in the session MCP registry. The `gh` CLI is available and `gh auth status` reported a signed-in `bunny0arch` account; token values were not recorded. This provides a usable GitHub route without falsely claiming a GitHub MCP server is installed.
6. No dedicated Filesystem MCP is listed. Manus file tools provide read/write/edit capabilities; Git and shell are available in this sandbox.
7. Exa and Sequential Thinking MCP servers are not listed in the session registry. The platform has web search and native reasoning/orchestration alternatives, which are not equivalent to claiming those named MCPs are installed.
8. Optional Figma, Shadcn, and Memory MCPs are not listed. They will be evaluated only if they add value and can be configured safely; they are not mandatory for ORBIT's prompt or this toolkit.
9. The authenticated GitHub account was identified as `bunny0arch`. A read-only lookup found no existing `bunny0arch/orbit-mcp-toolkit` repository at the time of the check.
10. The root project directory and Git repository have been initialized locally for this documentation baseline. No remote repository has yet been created.

## Execution sequence

### Checkpoint 0 — Documentation first

- Establish this private repository and commit the plan, current verified inventory, restoration notes, ORBIT prompt analysis, and execution log before installing/configuring MCPs.
- Keep the initial commit as a durable recovery point if later work is interrupted.

### Checkpoint 1 — Verify official sources and compatibility

- Consult official provider documentation and maintained repositories for missing requested integrations.
- Prefer existing supported Manus integrations and use focused tool coverage instead of duplicating equivalent browser, file, or search capabilities.
- Verify the actual Playwright browser installation path and any official GitHub, Exa, Filesystem, and Sequential Thinking MCP registration options.

### Checkpoint 2 — Configure selectively

- Reuse already-available Context7, Playwright, Supabase, and Vercel integrations.
- Install/configure an additional MCP only if it can be grounded in official docs, is compatible with this Manus environment, materially adds the requested capability, and can be authenticated securely.
- Do not place secrets in repository files, shell command arguments, logs, or commits.
- Do not edit Supabase production resources or create Vercel resources during toolkit validation.

### Checkpoint 3 — Harmless validation

- Context7: retrieve current React documentation.
- Search: find a suitable public open-source React component repository (use Exa if genuinely installed; otherwise record use of the platform search alternative).
- GitHub: inspect a public repository without modifying it.
- Filesystem: create/read/delete a temporary test file only within this authorized workspace (use built-in file tools if no separate MCP is available).
- Playwright: install/verify the configured browser runtime, then open a harmless test page and inspect its accessibility snapshot or console.
- Supabase/Vercel: verify tool availability and authentication state through safe, read-only checks only; do not assume access to a specific project.
- Advanced reasoning: document whether Sequential Thinking MCP is installed or native planning/orchestration is the available substitute.

### Checkpoint 4 — Update the record

- Update `MCP_TOOLKIT.md` with actual names, source, installation method, version when observable, configuration location, permissions, authentication status, tools, validation result, and limitations.
- Append each significant result to `EXECUTION_LOG.md`.
- Add a restoration guide that does not leak credentials.
- Clearly distinguish “available in session”, “installed/configured”, “authenticated”, and “validated”.

## Guardrails

- Preserve existing working connectors and settings.
- Never claim an MCP is installed merely because an entry or config draft exists.
- Request user authorization only when a provider requires credential entry, OAuth consent, or an external confirmation card.
- Ask before destructive database actions; none are part of this task.
- Use a private GitHub repository by default; do not publish the prompt or toolkit publicly without explicit instruction.
- The private GitHub repository is for docs and checkpoints, not a reason to commit secrets or private student/institutional data.
- Make no ORBIT implementation claims; application development remains a separate scope.

## Open questions to resolve from official sources

- Whether the Manus connector configuration supports the desired official GitHub MCP server in this session and what its exact OAuth flow requires.
- Whether Exa offers a suitable official hosted MCP flow and what authentication is required.
- Whether the requested filesystem and sequential-thinking MCPs would add meaningful capabilities beyond existing Manus tools and workflow, and whether their official implementations are maintainable/compatible.
- Which Playwright browser runtime `browser_install` is configured to install and whether that operation is available in the current MCP server.

## Completion definition

The toolkit task is complete only when available integrations have been tested harmlessly, unavailable/blocked integrations are explained with practical alternatives, the private GitHub repository has an accurate status record, and no MCP or application capability is overstated.
