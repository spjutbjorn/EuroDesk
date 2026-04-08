# Documenso

**Category:** E-signing
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU)
**Website:** [documenso.com](https://documenso.com)

## What It Is

Documenso is an open-source electronic signature platform for sending, signing, and tracking documents. It is a practical European alternative to DocuSign for internal approvals, contracts, HR forms, and customer-facing signatures.

## EU Hosting Options

| Option | Description |
|---|---|
| **Documenso Cloud** | Managed service from an EU vendor |
| **Self-hosted** | Run on your own EU infrastructure |

## Good Fit For

- Employment agreements
- Supplier contracts
- NDA workflows
- Internal approval chains

## Self-Hosted Setup

### Requirements
- Docker and Docker Compose
- PostgreSQL
- SMTP server for notifications

### Docker Compose Example

```yaml
version: "3.8"

services:
  postgres:
    image: postgres:16
    restart: unless-stopped
    environment:
      POSTGRES_DB: documenso
      POSTGRES_USER: documenso
      POSTGRES_PASSWORD: change-me
    volumes:
      - ./postgres:/var/lib/postgresql/data

  documenso:
    image: documenso/documenso:latest
    restart: unless-stopped
    ports:
      - "3005:3000"
    environment:
      DATABASE_URL: postgresql://documenso:change-me@postgres:5432/documenso
      NEXTAUTH_URL: https://sign.your-company.eu
      NEXTAUTH_SECRET: change-me-long-random-secret
      SMTP_HOST: smtp.your-company.eu
      SMTP_PORT: 587
      SMTP_USERNAME: sign@your-company.eu
      SMTP_PASSWORD: your-smtp-password
      SMTP_FROM_NAME: EuroDesk Sign
      SMTP_FROM_ADDRESS: sign@your-company.eu
    depends_on:
      - postgres
```

### Start

```bash
docker compose up -d
```

## Recommended Controls

- Require signed audit trails
- Store completed PDFs in your document platform
- Restrict public templates to approved admins
- Retain signed documents in backups

## Plans (2026)

| Plan | Price (Month) | Limits |
|---|---|---|
| **Free** | $0 | 5 documents /mo |
| **Individual** | $30 | Unlimited signing |
| **Teams** | $40 | 5 users included |
| **Self-Hosted** | Free | Unlimited, full control |

> **Note:** The self-hosted version is available under the AGPL license, allowing for complete data sovereignty on your own EU infrastructure.

## Key Features

- Request signatures from multiple parties
- Track status and audit trail
- Self-hosted option
- Simple API and team workflows
- Open source

## Trade-offs

- Review local legal requirements before relying on advanced signatures
- You may still need identity verification workflows for higher-assurance use cases
- Self-hosting means handling email delivery and storage retention

## Compliance Notes

- **Jurisdiction:** Documenso is a German company, fully subject to the GDPR.
- **Data Sovereignty:** All data is processed and stored on EU-based infrastructure in both managed and self-hosted deployments.
- **Privacy:** As an open-source tool, it minimizes data collection and supports self-hosting for maximum privacy.
- **Legal Compliance:** Supports European standards for electronic signatures (eIDAS). Review your local legal needs for specific signature levels (SES, AES, QES).

## EuroDesk Verdict

Documenso closes a common office gap: document signing without defaulting to a US platform.
