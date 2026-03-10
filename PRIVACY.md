# Privacy Policy

**SCM Accounting Automation**
**Effective Date: March 10, 2026**

## 1. Introduction

This Privacy Policy describes how SCM Accounting Automation ("the Application") handles data when connecting to QuickBooks Online via the Intuit API.

## 2. Data We Access

The Application accesses the following data from your QuickBooks Online account:
- Company information
- Chart of accounts
- Financial reports (Profit & Loss, Balance Sheet, Trial Balance)
- Transaction records (invoices, bills, expenses, journal entries)

## 3. How We Use Data

Data is accessed solely for:
- Viewing and reviewing accounting information
- Generating financial reports
- Educational and capstone project purposes

## 4. Data Storage

- QuickBooks data is accessed in real-time and is **not stored permanently** by the Application
- OAuth credentials (Client ID, Client Secret, Refresh Token) are stored locally on the developer's machine in a `.env` file and are never committed to version control
- No data is stored in any external database or cloud service

## 5. Data Sharing

We do **not** sell, share, or disclose your QuickBooks data to any third parties.

## 6. Security

- Credentials are excluded from version control via `.gitignore`
- OAuth 2.0 is used for secure authentication with Intuit
- All API communication uses HTTPS encryption

## 7. Your Rights

You may revoke this Application's access to your QuickBooks data at any time by:
- Removing the app connection from your QuickBooks Online account (Settings > Manage Apps)
- Revoking access at [developer.intuit.com](https://developer.intuit.com)

## 8. Changes to This Policy

This policy may be updated as the project evolves. Changes will be reflected in this document with an updated effective date.

## 9. Contact

For questions about this policy, contact the project owner via the [GitHub repository](https://github.com/Mitch-scm/SCM-Accounting-Automation).
