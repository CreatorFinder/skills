---
name: check-creator-finder
description: Check an existing Creator Finder data MCP connection and account allowance with one read-only usage call. Use for setup diagnostics; does not acquire creator data or start research.
---

# Check Creator Finder

Inspect the connected tool catalog for Creator Finder's `list_data_usage` on the configured `/mcp/data` connector. Use its exposed namespace and schema, never guess a tool identifier. Call it once with `{}`. This is the only service call authorized by this diagnostic: it does not reserve a data attempt or invoke a provider. Do not call discovery, profile, content, research, or outreach tools to test the connection.

Report:
- If usage returns a nonnegative integer `reservedAttempts` and explicit nonnegative integer `maxAttempts`, report attempts used and `max(0, maxAttempts - reservedAttempts)` remaining.
- Only explicit `maxAttempts: null` means no account pilot cap. Report attempts used; provider limits and the user's finite task budget still apply.
- Missing, malformed, failed or unavailable usage is unknown, never zero or unlimited. Do not expose raw error text, tokens or private tool metadata in the report.

If the tool is missing, tell the user to enable the data connector and reload its tools. If authentication fails, identify the existing connection method. API-key clients should check or replace their key through the CF workspace and their client’s secure MCP settings. Cowork browser-approved connections should reconnect, sign in to CF and explicitly approve data access. Do not direct API-key users in Codex, local Work or Claude Code into unsupported browser sign-in. ChatGPT web/cloud Work currently lacks CF authentication support; workspace skills import alone does not enable this check. Never ask for passwords, tokens or API keys in chat, documents or plugin files. The user can review or revoke access in Creator Finder Connections → Connected applications. For missing pilot permission, disabled service or unavailable history, report the specific safe condition and ask the team to check access. Never substitute legacy `/mcp` tools or retry through a paid data request.

The plugin contains public entrypoints that retrieve authenticated workflow instructions; the customer's own agent executes them. A successful diagnostic verifies this connection and allowance only, not every workflow or external provider. Only assess optional external tools when a requested workflow requires them. OAuth approval is for data access only; API keys used by other clients retain their existing permissions.
