
## 2026-11-05 — Filesystem MCP enabled and scoped

- Created and enabled `Filesystem MCP` using the official `@modelcontextprotocol/server-filesystem@2.2.0` package under isolated Node v24.22.2. Its only allowed directory is `/home/ubuntu/orbit-mcp-toolkit`.
- Enumerated the exposed tools and called the read-only `list_allowed_directories` tool. It returned exactly `/home/ubuntu/orbit-mcp-toolkit`; no home-root or system paths were allowed.
- Connector UID: `d1277358-15cd-4f0b-a085-235dc5774724`. No file was created, overwritten, or deleted as part of validation.
