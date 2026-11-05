# Toolkit Setup and Restoration Guide

This repository documents a reusable MCP toolkit, but integrations and authentication are environment- and account-specific. Cloning the repo does not install, enable, or authenticate any connector. The live connector configuration is managed by Manus and is intentionally not committed here.

## Verified status snapshot — 2026-11-05

| Integration | Current result |
|---|---|
| Context7 | Active; React documentation lookup passed. |
| Playwright | Active; Firefox runtime installed; basic navigation and snapshot passed. |
| Supabase | Active and reports authenticated; 31 tools exposed; no project selected or modified. |
| Vercel | Active; 246 tools exposed; no team/project selected or modified. |
| GitHub | Built-in connector is enabled and `gh` CLI is authenticated. Repository create/push and public repo metadata read passed through CLI. No separate GitHub MCP server was exposed or added. |
| Filesystem MCP | Active, official package v2.2.0; scoped only to `/home/ubuntu/orbit-mcp-toolkit`; temporary write/read test passed. |
| Sequential Thinking MCP | Active, official package v2.1.1; thought logging disabled; harmless tool test passed. |
| Exa | Existing catalog connector is still disabled because the activation suggestion was not accepted. Do not retry or create an alternate connector without fresh user authorization. |
| Figma, Shadcn, Memory | Optional in the user-provided guide; deferred for the reasons recorded in `MCP_TOOLKIT.md`. |

## Principles

1. Inspect the active Manus MCP registry and connectors before adding anything. Reuse native integrations where they satisfy the use case.
2. Verify provider identity, official endpoint or installation instructions, maintenance, authentication model, runtime compatibility, permissions, and cost.
3. Prefer least privilege and harmless validation. Limit local filesystem servers to the exact project directory.
4. Keep credentials out of Git. Do not commit API keys, PATs, passwords, private keys, cookies, service-role credentials, or raw secret-bearing connector exports.
5. Treat “listed”, “configured”, “enabled”, “authenticated”, and “validated” as distinct states. Record observable evidence in `MCP_TOOLKIT.md` and dated outcomes in `EXECUTION_LOG.md`.

## Restoring native integrations

In a compatible Manus task, inspect `manus-config connector list` and `manus-mcp-cli` before making changes. Use `manus-config connector ensure "<provider>"` for existing native integrations such as Context7, Supabase, or Vercel. Complete authorization only through the provider/Manus authorization flow. Do not assume the current task's authentication persists in another task, and do not query or alter a production project merely to test connector presence.

## Restoring the local Filesystem MCP

The current connector runs the official `@modelcontextprotocol/server-filesystem@2.2.0` package with Node v24.22.2. The sandbox's default Node was v22.23.4, so the `node@24.22.2` npm package was used as an isolated runtime without replacing system Node. The server's only allowed directory was `/home/ubuntu/orbit-mcp-toolkit`.

When creating a connector in another workspace, change the final server argument to the exact absolute path of that project's repository. Never use `/home/ubuntu`, `/`, or a broad home directory as the allowed path. A secret-free stdio draft shape is:

```json
{
  "name": "Filesystem MCP",
  "description": "Read and manage project files, restricted to this repository folder.",
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "--yes",
        "--package=node@24.22.2",
        "--package=@modelcontextprotocol/server-filesystem@2.2.0",
        "mcp-server-filesystem",
        "/absolute/path/to/this/repository"
      ]
    }
  }
}
```

The current package exposes read/write/edit, search, copy/move, and directory tools, but no `delete_file` tool. For a temporary validation file, use a unique name and remove only that newly created file through a safe host-side cleanup after the write/read check.

## Restoring Sequential Thinking MCP

The current local connector uses `@modelcontextprotocol/server-sequential-thinking@2.1.1` under `node@24.22.2` and sets `DISABLE_THOUGHT_LOGGING=true`. Keep entries concise and high-level; do not put secrets or sensitive content in tool inputs. Its safe draft shape is:

```json
{
  "name": "Sequential Thinking MCP",
  "description": "Local structured planning tool for tasks that benefit from revisions or branching.",
  "note": "Use concise, high-level planning only. Do not include secrets or sensitive data. Thought logging is disabled.",
  "mcpServers": {
    "sequentialthinking": {
      "command": "npx",
      "args": [
        "--yes",
        "--package=node@24.22.2",
        "--package=@modelcontextprotocol/server-sequential-thinking@2.1.1",
        "mcp-server-sequential-thinking"
      ],
      "env": {
        "DISABLE_THOUGHT_LOGGING": "true"
      }
    }
  }
}
```

## GitHub, Exa, and optional integrations

Use the existing built-in GitHub connector and authorized `gh` CLI when available. In this task, `manus-mcp-cli` did not expose a separate `github` MCP server; the ensure flow selected the built-in connector, so a duplicate remote connector was not created. If a future task specifically needs GitHub's remote MCP, verify its official endpoint and host OAuth support first, then use the least-privileged read-only endpoint unless write access is explicitly required and approved. Never move a PAT from an existing credential store into repository files or an MCP draft.

The existing Exa catalog connector remains disabled because activation was not accepted. Do not bypass this by registering another Exa connector. Use platform search under its own name when appropriate. Figma is optional and requires an authorized account; Shadcn documentation can be reached through Context7/provider docs; Memory should be added only if it contributes value beyond Manus memory and the project repository.

## Validation and maintenance

Use `manus-mcp-cli tool list --server <name>` to check that the MCP host exposes tools, then inspect the exact schema before a test call. For a newly scoped filesystem connector, verify its allowed-directory list and perform a temporary write/read round trip. For Context7, use `resolve-library-id` before `query-docs`. For Supabase and Vercel, confirm the expected tool surface without querying or changing production resources. For browser testing, navigate to a harmless page and inspect a snapshot. Record outcomes, limits, versions, and any authorization the user declined; never overstate an unperformed test.

When a new MCP is installed, update `MCP_TOOLKIT.md`, append the event to `EXECUTION_LOG.md`, run `git diff --check`, scan documentation for secrets, and push the redacted docs to this private repository. Do not commit session-specific connector configuration or credentials.
