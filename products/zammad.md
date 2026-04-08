# Zammad

**Category:** Helpdesk / Ticketing
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU)
**Website:** [zammad.com](https://zammad.com)

## What It Is

Zammad is an open-source helpdesk and ticketing platform for support inboxes, internal service desks, and customer support workflows. It centralizes email, forms, and agent workflows while keeping data on European infrastructure you control.

## EU Hosting Options

| Option | Description |
|---|---|
| **Zammad Cloud** | Managed service in ISO27001 German data centers |
| **Self-hosted** | Run on your own EU server (Community or Enterprise support) |

## Plans (Zammad Hosted 2026)

| Plan | Price (Agent/Mo) | Agent Limit | Key Features |
|---|---|---|---|
| **Starter** | €7 (ann.) | 5 | Text modules, Macros, Branding |
| **Professional** | €16 (ann.) | 35 | SLAs, Single Knowledge Base |
| **Plus** | €25 (ann.) | Unlimited | Multilingual Knowledge Base, GitHub/Lab |

> **AI Add-on:** Optional AI features (summarization, auto-replies) are available on Professional and Plus plans for approx. €0.03 per AI call.

## Setup (Self-hosted)


- Internal IT helpdesk
- Customer support teams
- Shared support mailboxes
- SLA-driven ticket workflows

## Self-Hosted Setup

### Requirements
- Ubuntu server
- PostgreSQL
- Elasticsearch or OpenSearch
- SMTP and IMAP access

### Install

```bash
curl -fsSL https://dl.packager.io/srv/zammad/zammad/key | sudo gpg --dearmor -o /usr/share/keyrings/zammad.gpg
echo "deb [signed-by=/usr/share/keyrings/zammad.gpg] https://dl.packager.io/srv/deb/zammad/zammad/stable/ubuntu 22.04 main" | sudo tee /etc/apt/sources.list.d/zammad.list
sudo apt update
sudo apt install -y zammad
```

### Start

```bash
sudo systemctl enable --now zammad
```

### First Configuration

1. Connect your support email inbox
2. Define groups and queues
3. Set SLAs and triggers
4. Restrict admin access with SSO or MFA

## Key Features

- Email-to-ticket workflows
- Customer portal and agent UI
- Automations, triggers, and SLAs
- Reporting and search
- Self-hosted and managed deployment

## Trade-offs

- Search stack adds operational complexity
- Best results come from a clean ticket workflow design
- Large teams should plan permissions and queue structure early

## Compliance Notes

- **Jurisdiction:** Zammad GmbH is based in Berlin, Germany (EU).
- **Data Sovereignty:** Fully hostable on your own EU infrastructure. All tickets and agent logs stay on your servers.
- **Privacy:** As an open-source tool, you have full control over all personal data in support tickets.
- **GDPR:** Fully compliant as a German company. DPA available for Zammad Cloud users.

## EuroDesk Verdict

Zammad rounds out EuroDesk with a proper service desk layer for internal support and customer-facing ticket workflows.
