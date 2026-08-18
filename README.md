# Waqi — the MCP server that redacts PII before the AI sees it

**Waqi (واقي, "protector") is a hosted MCP server that sits between your business tools and your AI assistant.** Connect Stripe, Xero, your CRM and more to Claude or ChatGPT — Waqi fetches the data read-only, strips names, card numbers and personal details, writes a provable audit entry, and only then returns the cleaned data to the model.

Your AI gets real answers from real business data. Your customers' personal data never reaches it.

- **Website:** [bilazann.com/waqi](https://bilazann.com/waqi)
- **Setup guides:** [bilazann.com/waqi/docs](https://bilazann.com/waqi/docs)

> This is a **hosted, commercial** MCP server. This repository contains its documentation and MCP Registry manifest — the service itself runs at `waqi.bilazann.com`.

## How it works

```
AI assistant ──1· tool call──▶ Waqi ──2· read-only fetch──▶ Your tools (Stripe, Xero, CRM…)
     ▲                          │
     └──3· redacted data only───┘   (audit log written AFTER redaction —
                                     the sensitive values are never stored)
```

- **Redaction first.** Names, emails, phone numbers, card numbers, addresses and other personal identifiers are detected and replaced before the response leaves Waqi.
- **Provable audit log.** Every call is logged — who asked, which tool, how many sensitive items were caught — so you can show clients or regulators exactly what the AI never saw.
- **Per-person tokens.** Each team member gets their own MCP URL; every call is individually attributed, and access is revoked per person, not per company.
- **Read-only by design.** Waqi fetches; it never writes to your tools.
- **Credentials stay encrypted.** Connector keys are stored encrypted and are never visible to anyone — including us.

## Quickstart

You need a Waqi account ([start here](https://bilazann.com/waqi)) — the dashboard gives each team member a personal MCP URL of the form:

```
https://waqi.bilazann.com/api/mcp/YOUR_TOKEN
```

**Claude (web/desktop):** Settings → Connectors → *Add custom connector* → paste your MCP URL.

**Claude Code:**

```bash
claude mcp add --transport http waqi https://waqi.bilazann.com/api/mcp/YOUR_TOKEN
```

**ChatGPT:** Settings → Connectors → *Advanced* → *Developer mode* → add the same URL.

**Standard MCP configuration** (for clients that use a JSON config file):

```json
{
  "mcpServers": {
    "waqi": {
      "type": "http",
      "url": "https://waqi.bilazann.com/api/mcp/YOUR_TOKEN"
    }
  }
}
```

Step-by-step guides with screenshots for every client and every connector: [bilazann.com/waqi/docs](https://bilazann.com/waqi/docs).

> Tip: in Claude, an attached connector still has to be **enabled in the chat** you're using — if tools list but never run, that's the switch to check.

## Supported connectors

Stripe · Xero · Zoho Books · Zoho CRM · Slack · and more — 16 business tools across payments, accounting, CRM, and communication, with new connectors added on request ([current list](https://bilazann.com/waqi/docs)).

## Security & data handling

- Connector credentials: stored encrypted, write-only (no read-back UI, not even for the account owner).
- MCP tokens: only SHA-256 hashes are stored.
- Audit log: written post-redaction — the log itself never contains the sensitive values.
- Full detail: [bilazann.com/waqi#trust](https://bilazann.com/waqi#trust)

## Pricing

Self-serve, VAT-inclusive, from £99/month (annual and team plans available) — [bilazann.com/waqi](https://bilazann.com/waqi).

## Support

- Docs: [bilazann.com/waqi/docs](https://bilazann.com/waqi/docs)
- Contact: via the website

---

*Waqi is built by [Bilazann](https://bilazann.com). "Bilazann" means "without doubt" — Waqi is that idea applied to AI: use it fully, without doubting what it saw.*
