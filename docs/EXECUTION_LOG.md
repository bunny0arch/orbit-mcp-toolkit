
## 2026-11-05 — Connector configuration plan (not yet applied)

The next connector operations will be limited to the already-requested integrations and these exact settings:

- Exa: enable the existing catalog connector at the official `https://mcp.exa.ai/mcp` endpoint, then validate public search/fetch only. If OAuth authorization is requested, wait for the user to complete the provider card; do not seek or store an API key.
- GitHub: if a distinct custom MCP connector can be created, use `https://api.githubcopilot.com/mcp/readonly` only. Its OAuth flow is separate from the already-enabled built-in GitHub connector and `gh` CLI. Do not use a PAT or a write-capable endpoint.
- Filesystem: run `@modelcontextprotocol/server-filesystem@2.2.0` under `node@24.22.2` and allow only `/home/ubuntu/orbit-mcp-toolkit`; do not grant home-directory or system access.
- Sequential Thinking: if attached, run `@modelcontextprotocol/server-sequential-thinking@2.1.1` under `node@24.22.2` with `DISABLE_THOUGHT_LOGGING=true`. It remains optional and will be reported as pending if the host does not expose its tool.
- No ORBIT application, external service resource, database, deployment, or repository permission changes are included in this phase.

## 2026-11-05 — Exa activation outcome

- Ran the supported `connector ensure Exa` flow for the existing official catalog entry. The session reported that Exa remains disabled and that the original activation suggestion was not accepted.
- Respecting that choice: no second activation attempt and no alternate/custom Exa connector will be created. Use the existing platform web-search capability when source discovery is needed; label it accurately rather than calling it Exa.
- This outcome does not affect the separately requested GitHub, filesystem, Playwright, Supabase, Vercel, or Sequential Thinking checks.

## 2026-11-05 — GitHub MCP ensure outcome

- Submitted the GitHub official read-only endpoint through the documented `connector ensure` flow. Manus matched the request to the existing enabled built-in GitHub connector and reported it ready.
- No separate remote GitHub MCP was created, no OAuth/PAT was added, and no write-capable endpoint was configured. GitHub access for repository documentation is available through the authenticated CLI and built-in connector. This distinction remains explicit in the inventory.
