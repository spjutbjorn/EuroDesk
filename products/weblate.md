# Weblate

**Category:** Translation Management / Localization
**Type:** Self-hosted or managed
**Jurisdiction:** Czech Republic (EU)
**Website:** [weblate.org](https://weblate.org)

## What It Is

Weblate is an open-source translation management platform for handling multilingual websites, applications, and documentation. It is designed for collaborative localization workflows, glossary management, review, and synchronization with source repositories.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Weblate on your own EU-hosted infrastructure |
| **Weblate Hosted** | Use managed hosting from an EU vendor |

## Good Fit For

- Translation and localization teams
- Product and documentation teams
- NGOs and public organizations publishing in multiple languages
- Software localization linked to Git repositories

## Self-Hosted Setup

### Requirements
- Linux server
- PostgreSQL or MariaDB
- Redis
- Python runtime

### Docker Compose Example

```yaml
version: "3.8"

services:
  weblate:
    image: weblate/weblate:latest
    restart: unless-stopped
    ports:
      - "8087:8080"
    environment:
      WEBLATE_SITE_DOMAIN: translate.your-company.eu
      WEBLATE_ADMIN_EMAIL: admin@your-company.eu
      WEBLATE_EMAIL_HOST: smtp.your-company.eu
    volumes:
      - ./weblate-data:/app/data
```

### Start

```bash
docker compose up -d
```

## Plans (Cloud 2026)

| Plan | Price (Month) | Key Features |
|---|---|---|
| **Basic** | ~€19 | Up to 1,000 strings |
| **Standard** | ~€70 | Up to 10,000 strings |
| **Plus** | ~€193 | Up to 50,000 strings |

> **Note:** The self-hosted version of Weblate is free and open-source, providing full data ownership on your own EU infrastructure.

## Key Features

- Collaborative translation and review
- Glossaries, translation memory, and terminology management
- Git integration for software and documentation projects
- Role-based permissions and workflow states
- Self-hosted and managed options

## Compliance Notes

- Keep source content, translated assets, and terminology data on EU-controlled infrastructure.
- Restrict project access because localization often includes unreleased product or legal content.
- Review connector settings to avoid sending source material into non-EU external services.

## Trade-offs

- More operationally involved than simple machine-translation tools
- Best when translation is a recurring workflow rather than one-off text conversion
- Teams may still pair it with DeepL for assisted translation

## EuroDesk Verdict

Weblate fills a key gap for translation, localization, multilingual publishing, and public-sector communication workflows across Europe.
