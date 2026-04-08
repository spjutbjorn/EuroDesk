# n8n

**Category:** Automation / Workflows
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU)
**Website:** [n8n.io](https://n8n.io)

## What It Is

n8n is a workflow automation platform for connecting apps, moving data, and automating repetitive business processes. It is a strong fit for EuroDesk because it can replace Zapier-style SaaS automations while keeping sensitive workflows on EU-controlled infrastructure.

## EU Hosting Options

| Option | Description |
|---|---|
| **n8n Cloud** | Managed service from a German vendor |
| **Self-hosted** | Run on your own EU server or Kubernetes cluster |

## Good Fit For

- Syncing contacts and tickets between tools
- Sending alerts from monitoring to chat
- Routing signed documents to storage
- Automating onboarding and offboarding workflows

## Self-Hosted Setup

### Docker Compose Example

```yaml
version: "3.8"

services:
  n8n:
    image: docker.n8n.io/n8nio/n8n:latest
    restart: unless-stopped
    ports:
      - "5678:5678"
    environment:
      N8N_HOST: automation.your-company.eu
      N8N_PORT: 5678
      N8N_PROTOCOL: https
      WEBHOOK_URL: https://automation.your-company.eu/
      N8N_SECURE_COOKIE: "true"
      GENERIC_TIMEZONE: Europe/Stockholm
    volumes:
      - ./n8n-data:/home/node/.n8n
```

### Start

```bash
docker compose up -d
```

### Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name automation.your-company.eu;

    location / {
        proxy_pass http://localhost:5678;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## Recommended First Workflows

1. Ticket alerts to Mattermost or Matrix
2. Signed document archive to Nextcloud
3. Account provisioning notifications
4. Backup failure alerts to your helpdesk

## Key Features

- Visual workflow builder
- Large integration catalog
- Self-hosted execution
- Webhooks, schedules, and API triggers
- Useful glue for a multi-tool office stack

## Trade-offs

- Sensitive workflows require careful credential management
- Complex automations still need design and monitoring
- High-volume jobs may need queue and database tuning

## Compliance Notes

- **Jurisdiction:** n8n is based in Berlin, Germany (EU).
- **Data Sovereignty:** Fully hostable on your own EU infrastructure. All workflow and automation data stays on your servers.
- **Privacy:** As a self-hosted tool, you have full control over the data processed. Telemetry can and should be disabled in the configuration.
- **GDPR:** Fully compliant as a German company. DPA available for n8n Cloud users.

## EuroDesk Verdict

n8n is one of the most valuable missing pieces because it connects the rest of the stack into a working system.
