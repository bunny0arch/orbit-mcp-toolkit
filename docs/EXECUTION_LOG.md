
## 2026-11-05 — Connector configuration plan (not yet applied)

The next connector operations will be limited to the already-requested integrations and these exact settings:

- Exa: enable the existing catalog connector at the official `https://mcp.exa.ai/mcp` endpoint, then validate public search/fetch only. If OAuth authorization is requested, wait for the user to complete the provider card; do not seek or store an API key.
- GitHub: if a distinct custom MCP connector can be created, use `https://api.githubcopilot.com/mcp/readonly` only. Its OAuth flow is separate from the already-enabled built-in GitHub connector and `gh` CLI. Do not use a PAT or a write-capable endpoint.
- Filesystem: run `@modelcontextprotocol/server-filesystem@2.2.0` under `node@24.22.2` and allow only `/home/ubuntu/orbit-mcp-toolkit`; do not grant home-directory or system access.
- Sequential Thinking: if attached, run `@modelcontextprotocol/server-sequential-thinking@2.1.1` under `node@24.22.2` with `DISABLE_THOUGHT_LOGGING=true`. It remains optional and will be reported as pending if the host does not expose its tool.
- No ORBIT application, external service resource, database, deployment, or repository permission changes are included in this phase.
