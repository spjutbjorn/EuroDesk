# Mattermost

**Category:** Team Messaging
**Type:** Self-hosted or managed (EU region)
**Jurisdiction:** EU-hostable
**Website:** [mattermost.com](https://mattermost.com)

## What It Is

Mattermost is an open-source team messaging platform, often described as a self-hosted Slack alternative. It offers channels, direct messages, threads, file sharing, integrations, and a plugin ecosystem.

## Editions (2026)

| Edition | Price (User/Mo) | Best For |
|---|---|---|
| **Team Edition** | Free | Self-hosted, core messaging |
| **Entry** | Free | High-security (10k msg history limit) |
| **Professional** | ~$10 | SSO (SAML/OIDC), guest accounts |
| **Enterprise** | Custom | Compliance exports, High Availability |
| **Enterprise Adv.** | Custom | Air-gapped, Zero Trust, Private AI |

> **Note:** Version 11 (2026) includes deep AI integration for channel summaries and retrospective reports in the Enterprise tiers.

## Setup (Self-hosted with Docker)

### Requirements
- Docker and Docker Compose
- A domain name
- PostgreSQL (included in compose)

### docker-compose.yml

```yaml
version: "2.4"
services:
  postgres:
    image: postgres:15-alpine
    restart: unless-stopped
    volumes:
      - ./volumes/db:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: mattermost
      POSTGRES_PASSWORD: change-me
      POSTGRES_DB: mattermost

  mattermost:
    image: mattermost/mattermost-team-edition:latest
    restart: unless-stopped
    depends_on:
      - postgres
    ports:
      - "8065:8065"
    volumes:
      - ./volumes/app/mattermost/config:/mattermost/config
      - ./volumes/app/mattermost/data:/mattermost/data
      - ./volumes/app/mattermost/logs:/mattermost/logs
      - ./volumes/app/mattermost/plugins:/mattermost/plugins
    environment:
      MM_SQLSETTINGS_DRIVERNAME: postgres
      MM_SQLSETTINGS_DATASOURCE: postgres://mattermost:change-me@postgres/mattermost?sslmode=disable
      MM_BLEVESETTINGS_INDEXDIR: /mattermost/bleve-indexes
      MM_SERVICESETTINGS_SITEURL: https://chat.your-company.eu
```

### Start

```bash
docker compose up -d
```

### Reverse Proxy (nginx)

```nginx
upstream mattermost {
    server 127.0.0.1:8065;
    keepalive 32;
}

server {
    listen 443 ssl;
    server_name chat.your-company.eu;

    location ~ /api/v[0-9]+/(users/)?websocket$ {
        proxy_pass http://mattermost;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }

    location / {
        proxy_pass http://mattermost;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### Initial Setup

1. Navigate to `https://chat.your-company.eu`
2. Create the first admin account
3. Create your team/workspace
4. Invite team members via email

## Key Features

- Channels (public, private, read-only)
- Threads and threaded replies
- File and image sharing
- Search across message history
- Slash commands and bots
- Incoming/outgoing webhooks
- Plugin marketplace (Jira, GitHub, GitLab integrations)
- Desktop apps (Windows, macOS, Linux) and mobile apps

## Configuration Recommendations

### Disable Telemetry

In `config.json` or via admin console:

```json
{
  "LogSettings": {
    "EnableDiagnostics": false
  }
}
```

### Email Notifications

Configure SMTP to use an EU-hosted mail server (e.g., Mailbox.org SMTP or your own Postfix).

### Compliance Export

Enable compliance export under **System Console > Compliance > Compliance Export** for audit trails.

## Compliance Notes

- All messages and files stay on your infrastructure
- Role-based access control
- Audit logging for admin actions
- GDPR: built-in data export and user deletion tools
- E2E encryption available via plugin (experimental)

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Slack | US-hosted, data not EU-resident |
| Microsoft Teams | US company; EU residency is complex and costly |
| Discord | Consumer product, not business-grade |
