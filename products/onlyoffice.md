# ONLYOFFICE

**Category:** Office Suite / Document Editing
**Type:** Self-hosted or managed
**Jurisdiction:** EU-hostable; ONLYOFFICE is developed by Ascensio System SIA (Latvia, EU)
**Website:** [onlyoffice.com](https://www.onlyoffice.com)

## What It Is

ONLYOFFICE is a fully Microsoft Office-compatible open-source office suite. It supports `.docx`, `.xlsx`, `.pptx` and many other formats with real-time collaborative editing. It can be self-hosted as a Document Server and integrates with Nextcloud, Seafile, and other platforms.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted Document Server** | Run on any EU VPS |
| **ONLYOFFICE Cloud** | Managed SaaS, EU-region available |
| **Nextcloud + ONLYOFFICE** | Integrated into your Nextcloud instance |

## Plans (2026 Estimates)

| Product | Plan | Deployment | Pricing |
|---|---|---|---|
| **ONLYOFFICE Docs** | **Enterprise Cloud** | Cloud | ~$8.00 /user/mo |
| **ONLYOFFICE Docs** | **Enterprise Edition** | On-Prem | ~$1,200 (lifetime) |
| **ONLYOFFICE Workspace**| **Cloud Business** | Cloud | ~$20.00 /admin/mo |
| **ONLYOFFICE DocSpace** | **Business** | Cloud | ~$20.00 /admin/mo |

> **Note:** On-premises licenses are typically "Lifetime" for the version purchased, with one year of updates included. Workspace includes Mail, CRM, and Projects, while Docs focuses on the editing suite.

## Setup (Self-hosted Document Server with Docker)

### docker-compose.yml

```yaml
version: '3'

services:
  onlyoffice:
    image: onlyoffice/documentserver:latest
    restart: always
    ports:
      - "8081:80"
    volumes:
      - onlyoffice_data:/var/www/onlyoffice/Data
      - onlyoffice_logs:/var/log/onlyoffice
      - onlyoffice_fonts:/usr/share/fonts/truetype/custom
    environment:
      - JWT_ENABLED=true
      - JWT_SECRET=change-this-to-a-strong-secret
      - JWT_HEADER=AuthorizationJwt

volumes:
  onlyoffice_data:
  onlyoffice_logs:
  onlyoffice_fonts:
```

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
map $http_upgrade $connection_upgrade {
    default upgrade;
    '' close;
}

server {
    listen 443 ssl;
    server_name office.your-company.eu;

    location / {
        proxy_pass http://localhost:8081;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection $connection_upgrade;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

### Generate a JWT Secret

```bash
openssl rand -hex 32
```

Use the output as `JWT_SECRET`.

## Integrate with Nextcloud

1. In Nextcloud admin: **Apps** → Install **ONLYOFFICE**
2. **Settings** → **ONLYOFFICE**:
   - Document Editing Service address: `https://office.your-company.eu`
   - Secret key: same value as `JWT_SECRET`
3. Test the connection
4. Supported file types: `.docx`, `.xlsx`, `.pptx`, `.odt`, `.ods`, `.odp`, and more

## ONLYOFFICE Workspace (Full Suite)

For a complete groupware alternative, deploy ONLYOFFICE Workspace which includes:
- Document editing
- Email server
- Calendar
- CRM
- Project management

```bash
bash <(curl -s https://download.onlyoffice.com/install/workspace-install.sh)
```

This is an all-in-one script for Ubuntu. Always verify scripts before running.

## Key Features

- Full MS Office format compatibility (highest fidelity of any open-source alternative)
- Real-time co-editing (fast and tracked-changes mode)
- Comments, mentions, version history
- Form creation and filling
- Document comparison
- Mail merge
- Macro support (JavaScript-based)
- Desktop editors for Windows, macOS, Linux
- Mobile apps

## Performance Tuning

For teams over 50 concurrent users, increase connection limits in `local.json`:

```json
{
  "services": {
    "CoAuthoring": {
      "server": {
        "workerpercpu": 2
      }
    }
  }
}
```

## Compliance Notes

- Developed by Ascensio System SIA, registered in Latvia (EU)
- Self-hosted: all documents stay on your infrastructure
- JWT authentication prevents unauthorized document access
- GDPR: no document content sent to ONLYOFFICE servers in self-hosted mode
- Community Edition source code is fully open (AGPL-3.0)

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Microsoft Office 365 | US company; EU data boundary requires premium add-on |
| Google Docs | US company |
| LibreOffice Online (Collabora) | Good alternative; less MS Office compatible |
