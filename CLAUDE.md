# SCM Accounting Automation

## Project Purpose

Capstone project that integrates QuickBooks Online with Claude Code via the Model Context Protocol (MCP). Uses the `laf-rge/quickbooks-mcp` server to give Claude direct access to QBO for querying financial data, generating reports, and managing accounting transactions through natural language.

## Project Structure

```
Quickbooks/
├── quickbooks-mcp/    # Cloned MCP server (git submodule-like, do not edit)
├── .env               # QBO credentials (NEVER commit)
├── .mcp.json          # Claude Code MCP server configuration
├── CLAUDE.md          # This file — project conventions
└── README.md          # Project overview and setup guide
```

## Conventions

- **Read-only mode** — only use query and report tools (no create/edit/delete) until explicitly told otherwise
- **Do not edit files inside `quickbooks-mcp/`** — treat it as a dependency
- **Never commit `.env`** — it contains secrets; `.gitignore` excludes it
- **Draft mode is default** — all QBO write operations preview before committing; set `draft: false` only when explicitly confirmed
- **Monetary values use cents internally** — the MCP server handles conversion; always verify amounts before committing transactions
- Use imperative commit messages (e.g., "Add invoice query tool", not "Added...")

## MCP Server

The QuickBooks MCP server (`quickbooks-mcp/`) provides these key tools:
- `qbo_authenticate` — OAuth setup
- `query` — SQL-like queries across all QBO entities
- `get_profit_loss`, `get_balance_sheet`, `get_trial_balance` — financial reports
- `create_*` / `edit_*` / `get_*` — CRUD for journal entries, bills, expenses, invoices, deposits, sales receipts, vendor credits
- `delete_entity` — delete any transaction

## Authentication

1. Populate `.env` with QBO app credentials from developer.intuit.com
2. Alternatively, use `qbo_authenticate` tool for interactive OAuth flow
3. Credentials file: `~/.quickbooks-mcp/credentials.json`

## Development Workflow

1. Build the MCP server: `cd quickbooks-mcp && npm install && npm run build`
2. Restart Claude Code to load the MCP server
3. Test with `get_company_info` to verify connectivity
