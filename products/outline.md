# Outline

**Category:** Team Wiki & Knowledge Base
**Type:** Self-hosted or managed
**Jurisdiction:** EU-hostable; Outline Inc. is US-based but the software is fully self-hostable
**Website:** [getoutline.com](https://www.getoutline.com)

## What It Is

Outline is a fast, collaborative team wiki. It is the go-to developer knowledge base — used for internal documentation, runbooks, architecture decisions (ADRs), onboarding guides, and API references. It has a clean editor with real-time collaboration and supports Markdown natively.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Any EU VPS — open source (BSL license) |
| **Outline Cloud (EU)** | Managed SaaS, EU region available |

## Setup (Docker Compose)

### Prerequisites

Outline requires:
- PostgreSQL
- Redis
- An S3-compatible object store for file uploads (MinIO works, self-hosted)
- An OAuth2 or OIDC provider for login (or Slack/Google — use your own)

### docker-compose.yml

```yaml
version: "3"

services:
  outline:
    image: outlinewiki/outline:latest
    restart: unless-stopped
    ports:
      - "3003:3000"
    env_file:
      - .env
    depends_on:
      - postgres
      - redis
      - minio

  postgres:
    image: postgres:15-alpine
    restart: unless-stopped
    volumes:
      - ./postgres-data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: outline
      POSTGRES_USER: outline
      POSTGRES_PASSWORD: changeme

  redis:
    image: redis:7-alpine
    restart: unless-stopped

  minio:
    image: minio/minio:latest
    restart: unless-stopped
    volumes:
      - ./minio-data:/data
    environment:
      MINIO_ROOT_USER: outline-minio
      MINIO_ROOT_PASSWORD: changeme-minio
    command: server /data --console-address ":9001"
    ports:
      - "9002:9000"
      - "9001:9001"
```

### .env

```env
SECRET_KEY=changeme-use-openssl-rand-hex-32
UTILS_SECRET=changeme-use-openssl-rand-hex-32

DATABASE_URL=postgres://outline:changeme@postgres:5432/outline
REDIS_URL=redis://redis:6379

URL=https://wiki.your-company.eu
PORT=3000

# File storage (MinIO — S3-compatible)
AWS_ACCESS_KEY_ID=outline-minio
AWS_SECRET_ACCESS_KEY=changeme-minio
AWS_REGION=eu-central-1
AWS_S3_UPLOAD_BUCKET_URL=http://minio:9000
AWS_S3_UPLOAD_BUCKET_NAME=outline
AWS_S3_FORCE_PATH_STYLE=true
AWS_S3_ACL=private

# Email
SMTP_HOST=smtp.your-company.eu
SMTP_PORT=587
SMTP_USERNAME=wiki@your-company.eu
SMTP_PASSWORD=your-smtp-password
SMTP_FROM_EMAIL=wiki@your-company.eu
SMTP_SECURE=false

# Authentication — use one of the options below
# Option A: Slack (if you use Mattermost, use OIDC instead)
# SLACK_CLIENT_ID=
# SLACK_CLIENT_SECRET=

# Option B: Google (not EU — avoid)
# Option C: OIDC (recommended — use Authentik or Keycloak)
OIDC_CLIENT_ID=outline
OIDC_CLIENT_SECRET=your-oidc-secret
OIDC_AUTH_URI=https://auth.your-company.eu/application/o/authorize/
OIDC_TOKEN_URI=https://auth.your-company.eu/application/o/token/
OIDC_USERINFO_URI=https://auth.your-company.eu/application/o/userinfo/
OIDC_USERNAME_CLAIM=email
OIDC_DISPLAY_NAME=Company SSO
OIDC_SCOPES=openid profile email

# Misc
FORCE_HTTPS=true
ENABLE_UPDATES=false
```

### Generate Secrets

```bash
openssl rand -hex 32   # for SECRET_KEY
openssl rand -hex 32   # for UTILS_SECRET
```

### Create MinIO Bucket

```bash
# Install MinIO client
docker run --rm -it --network host minio/mc \
  alias set local http://localhost:9002 outline-minio changeme-minio

docker run --rm -it --network host minio/mc \
  mb local/outline

docker run --rm -it --network host minio/mc \
  anonymous set download local/outline
```

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name wiki.your-company.eu;

    client_max_body_size 100M;

    location / {
        proxy_pass http://localhost:3003;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
    }
}
```

## Authentication with Authentik (Recommended)

Use [Authentik](https://goauthentik.io) as your self-hosted OIDC provider for SSO across Outline, Grafana, Mattermost, and other tools.

1. Deploy Authentik (see its own Docker Compose setup)
2. Create an OAuth2/OIDC application in Authentik named "Outline"
3. Set the redirect URL to `https://wiki.your-company.eu/auth/oidc.callback`
4. Copy the client ID and secret into Outline's `.env`

## Plans (2026)

| Plan | Price (Month) | User Limit |
|---|---|---|
| **Open Source** | $0 | Unlimited (technical setup) |
| **Business (1-10)**| ~$10 | Up to 10 users, easier SSO |
| **Business (11-100)**| ~$79 | Up to 100 users, priority support |
| **Enterprise** | ~$249 | Up to 200 users, custom SLA |

> **Note:** For EuroDesk, the **Open Source** self-hosted version or the **Sovereign** on-premises tiers must be used to ensure EU data residency.

## Key Features

- Rich text editor (Notion-like) with Markdown support
- Real-time collaborative editing
- Collections and nested documents
- Full-text search across all docs
- Document templates
- Public sharing links (optional, per-document)
- Revision history and restore
- Backlinks between documents
- Import from Confluence, Notion, Markdown
- Integrations via API
- Slack/Mattermost notifications on doc updates

## Use Cases for Developers

| Use Case | Example |
|---|---|
| **Runbooks** | "How to deploy to production" |
| **Architecture decisions** | ADR-001: Why we chose PostgreSQL |
| **API documentation** | Internal API reference |
| **Onboarding** | New developer setup guide |
| **Incident post-mortems** | What happened, timeline, actions |
| **Team processes** | Code review guidelines, branching strategy |

## Backup

```bash
# Backup PostgreSQL
docker exec outline-postgres-1 pg_dump -U outline outline > outline-backup-$(date +%Y%m%d).sql

# Backup MinIO data
tar -czf outline-files-$(date +%Y%m%d).tar.gz ./minio-data
```

## Compliance Notes

- All wiki content and attachments on your EU infrastructure
- `ENABLE_UPDATES=false` prevents check-in to external servers
- OIDC auth keeps user management within your organization
- GDPR: documents and user data exportable via API
- Restrict access: documents are private by default; sharing requires explicit action

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Confluence | Atlassian, US company |
| Notion | US company, data not EU-resident |
| Google Sites | US company |
| Nuclino | US company |
| BookStack | Self-hosted alternative, simpler but less collaborative |
