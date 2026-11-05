
## 2026-11-05 — Source verification and runtime readiness

- Installed the missing Firefox browser runtime using the exact browser-specific command recommended by the Playwright MCP error. The MCP then opened official GitHub, Exa, filesystem, and Sequential Thinking documentation pages; a harmless `example.com` navigation and snapshot check passed.
- Saved first-party endpoint, authentication, scope, and package findings in `docs/SOURCE_RESEARCH.md`. The GitHub provider includes a read-only hosted endpoint; Exa supports keyless hosted search/fetch under a free rate limit.
- The current Manus connector catalog already has the built-in GitHub integration enabled and an official Exa MCP entry disabled. No connector state has been changed yet. `gh` CLI was used only for the already-requested private repository creation/push.
- Default Node is v22.23.4, while the current filesystem and Sequential Thinking package metadata each specify Node `>=24`. A temporary npm-provided Node v24.22.2 was resolved without replacing the system runtime. Planned local MCP process arguments will pin the verified package versions and restrict filesystem access to this repository; Sequential Thinking, if enabled, will disable thought logging.
- Before adding connectors, the next checkpoint will document the exact configuration plan. Exa will use the official hosted endpoint. GitHub will use only its read-only hosted endpoint and may require user OAuth authorization. No PAT or API key will be copied from the environment or committed.
