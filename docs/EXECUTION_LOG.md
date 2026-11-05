
## 2026-11-05 — Core validation exercise

- Context7 resolved `/reactjs/react.dev` and returned current official React `useState` documentation. Passed.
- Filesystem MCP completed the guide-requested temporary write/read round trip inside its single allowed directory. The server has no `delete_file` tool; the exact temporary file created by this test was removed host-side, and the Git worktree is clean.
- GitHub's built-in connector is enabled, but `manus-mcp-cli` reports no server named `github`. The authenticated `gh` CLI read public `reactjs/react.dev` repository metadata and had already created/pushed this private documentation repo. This is explicitly a CLI fallback, not a GitHub MCP test.
- Supabase exposed 31 tools and Vercel exposed 246 tools, including the expected project/database and deployment/runtime-log capabilities. No production project/resource was selected or modified.
- Playwright's harmless navigation and snapshot test passed earlier. Sequential Thinking's expected tool and safe high-level test call passed earlier. Exa remains untested because activation was not accepted.
