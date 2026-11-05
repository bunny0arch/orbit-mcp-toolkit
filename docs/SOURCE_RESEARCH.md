# MCP Provider Source Research

**Checked:** 2026-11-05 (IST), using official provider documentation and repository pages.  
**Purpose:** Ground connector decisions in first-party sources; the pages below were opened with the configured Playwright browser after its Firefox runtime was installed.

## GitHub MCP

GitHub's official setup page identifies its GitHub MCP server as a GitHub-provided, maintained integration. It recommends the hosted remote server for most users and notes that particular tools inherit the requirements of the underlying GitHub features. The official server repository was active at the time checked, with a latest commit displayed as Nov. 4, 2026. [1] [2]

The repository's remote-server guide lists `https://api.githubcopilot.com/mcp/` as the hosted endpoint and publishes read-only variants, including `https://api.githubcopilot.com/mcp/readonly` for the default toolset and `/mcp/x/all/readonly` for all available tools. GitHub says an MCP host using OAuth needs an OAuth/GitHub App configuration; it also documents PAT authentication for hosts that support remote MCP but do not support OAuth. To minimize privileges, any custom connector should use the default read-only endpoint. Existing `gh` authentication is not copied into an MCP connector or this repository. If Manus cannot complete OAuth, the built-in GitHub connector and CLI remain the working repository workflow; do not add an unprovided PAT. [2] [3]

## Exa MCP

Exa's official guide publishes the hosted endpoint `https://mcp.exa.ai/mcp`. It supports keyless search and fetch at a free rate limit. OAuth (`?login`) or an `x-api-key` header is required for Exa Agent and authenticated usage. The default hosted tools include web search and fetch; advanced search can be opted in. Exa's documentation links to its first-party `exa-labs/exa-mcp-server` source repository. [4]

The current toolkit need is technical web discovery and source inspection, so the keyless hosted endpoint is sufficient for an initial least-privilege setup. The catalog already contains an Exa connector pointed at the official endpoint, but it is disabled. Enabling it may use the connector's OAuth flow; if a card requests authorization, wait for that step before testing.

## Filesystem MCP

The MCP maintainers publish `@modelcontextprotocol/server-filesystem` as a Node.js MCP server. Its documented features include file reads/writes, directory operations, search, and metadata. Every allowed directory should be passed as a server argument. The docs recommend that method across protocol versions; `--read-only` removes write-capable tools. [5]

The npm registry reported v2.2.0 with engine requirement `node >=24`. The sandbox's default Node is v22.23.4, but a scoped `npx --package=node@24 node --version` probe resolved Node v24.22.2 without replacing the system runtime. A possible local connector can therefore run the published server under Node 24 while limiting access strictly to `/home/ubuntu/orbit-mcp-toolkit`.

## Sequential Thinking MCP

The MCP maintainers' repository currently contains `src/sequentialthinking`, publishes `@modelcontextprotocol/server-sequential-thinking`, and describes its stepwise reasoning tool. The checked README's latest commit was Nov. 4, 2026. It supports stdio and recommends Node.js 24 or later when launched with `npx`; it is MIT-licensed. [6]

The npm registry reported v2.1.1 with engine requirement `node >=24`; the same isolated Node v24.22.2 probe succeeded. If attached, the connector should set `DISABLE_THOUGHT_LOGGING=true` to avoid writing thought content to stderr. This MCP is optional because native reasoning and workflow orchestration already exist; it should be activated only if its dedicated tool appears in the active host and adds concrete value.

## Playwright runtime

The active Playwright MCP requested Firefox v1569, but its executable was initially missing. The server did not expose a `browser_install` tool. The error recommended `npx --yes @playwright/mcp install-browser firefox`; this browser-specific command completed successfully and downloaded Firefox 158.0 plus FFmpeg into the Playwright cache. Playwright then opened the official GitHub, Exa, filesystem, and Sequential Thinking documentation pages, and a harmless `https://example.com` check rendered successfully. The integration is validated for basic navigation and snapshot access.

**Package metadata cross-check:** npm reports `@modelcontextprotocol/server-filesystem@2.2.0` and `@modelcontextprotocol/server-sequential-thinking@2.1.1`, each requiring Node.js `>=24`; both publish a named stdio executable. The sandbox default is Node v22.23.4. `npx --yes --package=node@24 node --version` returned v24.22.2, confirming an isolated compatible runtime can be resolved without upgrading the system Node installation.

## References

[1]: https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/set-up-the-github-mcp-server "Setting up the GitHub MCP Server"
[2]: https://github.com/github/github-mcp-server "GitHub's official MCP Server repository"
[3]: https://github.com/github/github-mcp-server/blob/main/docs/remote-server.md "Remote GitHub MCP Server documentation"
[4]: https://exa.ai/docs/get-started/exa-mcp "Exa MCP documentation"
[5]: https://github.com/modelcontextprotocol/servers/blob/main/src/filesystem/README.md "Filesystem MCP Server README"
[6]: https://github.com/modelcontextprotocol/servers/blob/main/src/sequentialthinking/README.md "Sequential Thinking MCP Server README"
