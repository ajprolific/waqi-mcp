# Waqi — AI Privacy Layer

## Tagline
Redacts PII from your business tools before the AI sees them — with a provable audit log.

## Description
Waqi (واقي, "protector") is a hosted MCP server that sits between your business tools and your AI assistant. Connect Stripe, Xero, your CRM and more to Claude or ChatGPT — Waqi fetches the data read-only, strips names, card numbers and personal details, writes a provable audit entry, and only then returns the cleaned data to the model. Your AI gets real answers from real business data; your customers' personal data never reaches it. Built for businesses whose teams already use AI: each team member gets their own protected link, and every call is individually attributed in the audit log. Nothing to install or host — sign up, connect a tool, paste your URL.

## Setup Requirements
- `token` (required): Your personal Waqi MCP token, embedded in your MCP URL (`https://waqi.bilazann.com/api/mcp/YOUR_TOKEN`). Generate it in the dashboard after signing up. https://bilazann.com/waqi

## Category
Security

## Use Cases
Data protection, Compliance, Revenue analysis, Client reporting, Team AI enablement, Finance Q&A, Audit trails

## Features
- Redaction before the model — PII is detected and replaced before any response leaves Waqi
- Provable audit log — every call logged (who asked, which tool, what was caught), written after redaction so the log never holds sensitive values
- Per-person MCP tokens — individual attribution, per-person revocation
- Read-only by design — Waqi fetches; it never writes to your tools
- Encrypted, write-only credential storage — connector keys are never visible to anyone, including the account owner
- 16 business connectors across payments, accounting, CRM and communication
- Works with Claude, ChatGPT (developer mode), Cursor, and any MCP-compatible client
- Self-serve setup in minutes — no IT project, no sales call

## Getting Started
- "List my recent Stripe charges" — returns real charge data with names and card details redacted
- "What were my top Xero invoices this month?" — real figures, zero client PII
- "Summarise my CRM pipeline" — deal data with contacts anonymised
- Tool: per-connector read tools (e.g. stripe list_charges) — fetch live business data through the redaction layer

## Tags
privacy, security, pii, redaction, data-protection, dlp, gdpr, compliance, audit, guardrails, stripe, xero, crm, accounting, business

## Documentation URL
https://bilazann.com/waqi/docs
