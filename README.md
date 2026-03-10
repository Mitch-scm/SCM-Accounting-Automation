# SCM Accounting Automation

A capstone project integrating QuickBooks Online with Claude Code using the Model Context Protocol (MCP). Enables AI-driven accounting workflows — query financial data, generate reports, and manage transactions through natural language.

## Overview

This project uses the [quickbooks-mcp](https://github.com/laf-rge/quickbooks-mcp) server to connect Claude Code directly to QuickBooks Online. Key capabilities:

- **Financial Reports** — Pull Profit & Loss, Balance Sheet, and Trial Balance reports
- **Natural Language Queries** — SQL-like queries across all QBO entities
- **Transaction Management** — Create and edit journal entries, bills, invoices, expenses, deposits, and more
- **Safe by Default** — All write operations use draft/preview mode before committing

## Prerequisites

- [Node.js 18+](https://nodejs.org/)
- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code)
- [QuickBooks Developer Account](https://developer.intuit.com)
- Git

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/SCM-Accounting-Automation.git
cd SCM-Accounting-Automation
```

### 2. Install and Build the MCP Server

```bash
cd quickbooks-mcp
npm install
npm run build
cd ..
```

### 3. Configure Environment Variables

Copy the `.env` template and fill in your QuickBooks credentials:

```bash
cp .env.example .env
```

Required variables:

| Variable | Description |
|----------|-------------|
| `QUICKBOOKS_CLIENT_ID` | OAuth Client ID from developer.intuit.com |
| `QUICKBOOKS_CLIENT_SECRET` | OAuth Client Secret |
| `QUICKBOOKS_REFRESH_TOKEN` | OAuth Refresh Token (from OAuth playground) |
| `QUICKBOOKS_COMPANY_ID` | Your QBO Company/Realm ID |
| `QUICKBOOKS_ENV` | `sandbox` or `production` |

### 4. Authenticate with QuickBooks

Option A — Use the MCP `qbo_authenticate` tool interactively from Claude Code.

Option B — Manually create `~/.quickbooks-mcp/credentials.json`:

```json
{
  "client_id": "your_client_id",
  "client_secret": "your_client_secret"
}
```

Then use `qbo_authenticate` in Claude Code to complete the OAuth flow.

### 5. Verify Setup

Open Claude Code in the project directory and run:

```
get_company_info
```

If configured correctly, you'll see your QBO company details.

## MCP Configuration

The `.mcp.json` file configures Claude Code to use the local QuickBooks MCP server:

```json
{
  "mcpServers": {
    "quickbooks": {
      "command": "node",
      "args": ["quickbooks-mcp/dist/index.js"]
    }
  }
}
```

## Available Tools

| Category | Tools |
|----------|-------|
| Setup | `qbo_authenticate`, `get_company_info` |
| Reports | `get_profit_loss`, `get_balance_sheet`, `get_trial_balance` |
| Queries | `query`, `list_accounts`, `query_account_transactions`, `account_period_summary` |
| Journal Entries | `create_journal_entry`, `get_journal_entry`, `edit_journal_entry` |
| Bills | `create_bill`, `get_bill`, `edit_bill` |
| Expenses | `create_expense`, `get_expense`, `edit_expense` |
| Invoices | `create_invoice`, `get_invoice`, `edit_invoice` |
| Sales Receipts | `create_sales_receipt`, `get_sales_receipt`, `edit_sales_receipt` |
| Deposits | `create_deposit`, `get_deposit`, `edit_deposit` |
| Vendor Credits | `create_vendor_credit`, `get_vendor_credit`, `edit_vendor_credit` |
| Delete | `delete_entity` |

## License

This project is for educational/capstone purposes.
