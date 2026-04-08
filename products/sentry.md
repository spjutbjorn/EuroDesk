# Sentry (Self-hosted)

**Category:** Error Tracking & Application Monitoring
**Type:** Self-hosted
**Jurisdiction:** EU-hostable when self-hosted; sentry.io managed is US-hosted
**Website:** [sentry.io](https://sentry.io) / [github.com/getsentry/self-hosted](https://github.com/getsentry/self-hosted)

## What It Is

Sentry captures and aggregates errors, exceptions, and crashes from your applications in real-time. It shows stack traces, release information, affected users, and breadcrumbs leading up to the error. It supports virtually every programming language and framework.

> **Note:** The managed sentry.io is US-hosted. Only the self-hosted version qualifies for EuroDesk.

## Setup (Self-hosted)

### Requirements

- Docker and Docker Compose
- **Minimum:** 4 CPU cores, 8 GB RAM, 20 GB disk
- **Recommended for production:** 4 cores, 16 GB RAM, 100 GB disk
- A domain name

### Install

```bash
git clone https://github.com/getsentry/self-hosted.git
cd self-hosted

# Run the install script
./install.sh
```

The script will:
1. Pull all required Docker images
2. Run database migrations
3. Prompt you to create an admin user

### Configuration

Edit `.env` before running `./install.sh`:

```env
SENTRY_EVENT_RETENTION_DAYS=90
COMPOSE_PROJECT_NAME=sentry

# Your domain
SENTRY_SERVER_NAME=errors.your-company.eu

# Email
SENTRY_EMAIL_HOST=smtp.your-company.eu
SENTRY_EMAIL_PORT=587
SENTRY_EMAIL_USER=errors@your-company.eu
SENTRY_EMAIL_PASSWORD=your-smtp-password
SENTRY_EMAIL_USE_TLS=True
SENTRY_SERVER_EMAIL=errors@your-company.eu
```

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name errors.your-company.eu;

    location / {
        proxy_pass http://localhost:9000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
    }
}
```

## Integrating Sentry into Your Apps

### JavaScript / TypeScript

```bash
npm install @sentry/browser
# or for Node.js
npm install @sentry/node
```

```typescript
import * as Sentry from "@sentry/browser";

Sentry.init({
  dsn: "https://<key>@errors.your-company.eu/<project-id>",
  environment: process.env.NODE_ENV,
  release: process.env.APP_VERSION,
  tracesSampleRate: 0.1,   // 10% of transactions traced
});
```

### Python

```bash
pip install sentry-sdk
```

```python
import sentry_sdk

sentry_sdk.init(
    dsn="https://<key>@errors.your-company.eu/<project-id>",
    environment="production",
    release="1.0.0",
    traces_sample_rate=0.1,
)
```

### Go

```bash
go get github.com/getsentry/sentry-go
```

```go
import "github.com/getsentry/sentry-go"

sentry.Init(sentry.ClientOptions{
    Dsn:         "https://<key>@errors.your-company.eu/<project-id>",
    Environment: "production",
    Release:     "1.0.0",
})
```

### PHP (Laravel)

```bash
composer require sentry/sentry-laravel
```

In `.env`:

```env
SENTRY_LARAVEL_DSN=https://<key>@errors.your-company.eu/<project-id>
```

### Docker / Container Apps

Use environment variables to avoid hardcoding DSNs:

```yaml
environment:
  SENTRY_DSN: "https://<key>@errors.your-company.eu/<project-id>"
  SENTRY_ENVIRONMENT: "production"
  SENTRY_RELEASE: "${APP_VERSION}"
```

## Creating a Project

1. Log into Sentry at `https://errors.your-company.eu`
2. **Projects** → **Create Project**
3. Choose your platform (JavaScript, Python, Go, etc.)
4. Copy the DSN shown in the setup guide
5. Use the DSN in your app's Sentry initialization

## Source Maps (JavaScript)

Upload source maps so Sentry can show readable stack traces:

```bash
npx @sentry/cli sourcemaps upload \
  --org your-org \
  --project your-project \
  --url-prefix "~/" \
  ./dist
```

In CI (Forgejo Actions):

```yaml
- name: Upload source maps to Sentry
  env:
    SENTRY_AUTH_TOKEN: ${{ secrets.SENTRY_AUTH_TOKEN }}
    SENTRY_ORG: your-org
    SENTRY_PROJECT: your-project
  run: |
    npx @sentry/cli releases new "$VERSION"
    npx @sentry/cli sourcemaps upload --release "$VERSION" ./dist
    npx @sentry/cli releases finalize "$VERSION"
```

## Alerting

**Project Settings** → **Alerts** → **Create Alert**:

- **Error rate spike**: alert when errors exceed a threshold
- **New issues**: alert on first occurrence of new error type
- **Regression**: alert when a previously resolved issue reappears

Send alerts to Mattermost via webhook:

**Settings** → **Integrations** → **Webhook** → Add your Mattermost incoming webhook URL.

## Key Features

- Real-time error capture with full stack traces
- User context: see which users are affected
- Release tracking: know which deploy introduced an issue
- Issue grouping (deduplication)
- Performance monitoring (transaction tracing)
- Breadcrumbs: events leading up to the error
- Source map support (readable JS stack traces)
- Session replay (optional, requires user consent for GDPR)
- Cron monitoring

## Maintenance

```bash
# Upgrade
cd self-hosted
git pull
./install.sh
docker compose up -d

# Clean old data
docker compose run --rm web cleanup
```

## Compliance Notes

- All error data stays on your EU infrastructure
- Disable session replay or obtain explicit user consent (GDPR)
- Error payloads may contain personal data — configure data scrubbing
- **Data Scrubbing**: **Project Settings** → **Security & Privacy** → enable PII scrubbing
- Event retention configurable (default 90 days)
- Self-hosted Sentry has no phone-home telemetry when `SENTRY_BEACON` is disabled

```env
# Disable beacon (telemetry) in .env
SENTRY_BEACON=false
```

## Alternatives Considered

| Alternative | Why not |
|---|---|
| sentry.io (managed) | US-hosted, error data including stack traces leaves EU |
| Bugsnag | US company |
| Rollbar | US company |
| Raygun | New Zealand company |
| Glitchtip | Self-hosted Sentry-compatible alternative, lighter weight |
