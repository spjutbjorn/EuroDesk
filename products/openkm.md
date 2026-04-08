# OpenKM

**Category:** Document Workflow / Records Management
**Type:** Self-hosted or managed
**Jurisdiction:** Spain (EU)
**Website:** [openkm.com](https://www.openkm.com)

## What It Is

OpenKM is a document management and records workflow platform for versioning, metadata, approvals, search, retention, and controlled business processes. It is useful for legal, compliance, public administration, and records-heavy teams that need more workflow structure than lightweight document archives.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run OpenKM on your own EU-hosted infrastructure |
| **Managed by EU provider** | Use a hosted deployment operated in the EU |

## Good Fit For

- Legal and compliance teams
- Public-sector records workflows
- Contract and policy approval chains
- Structured document retention and audit trails

## Self-Hosted Setup

### Requirements
- Linux server
- Java runtime
- Tomcat
- MySQL or PostgreSQL

### Install

```bash
# Download the current Community installer from the official OpenKM download page
# https://www.openkm.com/en/download.html

java -jar OKMInstaller.jar
```

The official Community download currently ships as `OKMInstaller.jar`, which guides the installation. Follow the OpenKM documentation for database selection, Tomcat integration, and upgrade steps.

## Key Features

- Document versioning and metadata
- Workflow automation and approval routing
- Full-text search and audit trails
- Retention-oriented records handling
- Self-hosted and managed deployment options

## Compliance Notes

- Use EU-owned hosting for legal files, records, and regulated internal documents.
- Configure retention, destruction, and audit policies according to sector requirements.
- Restrict admin and workflow access with SSO and role-based permissions.

## Trade-offs

- Heavier than lightweight personal or team document tools
- Best for controlled business processes rather than casual note-taking
- Requires metadata design and governance to deliver full value

## EuroDesk Verdict

OpenKM closes an important gap for law firms, public administration, and records-heavy organizations that need workflow-rich document control under EU jurisdiction.
