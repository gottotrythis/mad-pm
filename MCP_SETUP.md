# MCP Setup

The workspace-level MCP configuration currently lives in [`.vscode/mcp.json`](/Users/vaibhavjha/Documents/mad-pm/.vscode/mcp.json).

## Setup guidance

1. Add the MCP servers you use across projects in `.vscode/mcp.json`.
2. Prefer workspace-scoped config over machine-only setup so the repo stays portable.
3. Document any required credentials or environment variables in your personal notes, not in this repository.

## Recommended tool categories

- Research and browsing
- Docs and knowledge retrieval
- Jira, Linear, or task systems
- Slack or communication tools
- Drive, Notion, or document repositories
- Analytics or observability connectors

## Rule of thumb

If a tool is used across multiple projects, configure it at the workspace level.
If a tool is unique to one engagement, document it inside that project's folder.
