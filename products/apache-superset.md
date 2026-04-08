# Apache Superset

**Category:** BI / Dashboards
**Type:** Self-hosted
**Jurisdiction:** EU-hostable when self-hosted
**Website:** [superset.apache.org](https://superset.apache.org)

## What It Is

Apache Superset is an open-source business intelligence and dashboard platform for exploring data, building charts, and sharing reports with teams. It fills the business analytics gap in EuroDesk when you want dashboards on EU-hosted infrastructure instead of sending internal metrics to an external analytics SaaS.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Superset on your own EU-owned infrastructure |

## Good Fit For

- Sales and pipeline dashboards
- Support and SLA reporting
- Finance and invoicing analytics
- Operational KPI dashboards

## Self-Hosted Setup

### Requirements
- Docker and Docker Compose
- PostgreSQL or MySQL
- Redis

### Docker Compose Example

```yaml
version: "3.8"

services:
  db:
    image: postgres:16
    restart: unless-stopped
    environment:
      POSTGRES_DB: superset
      POSTGRES_USER: superset
      POSTGRES_PASSWORD: change-me
    volumes:
      - ./postgres:/var/lib/postgresql/data

  redis:
    image: redis:7
    restart: unless-stopped

  superset:
    image: apache/superset:latest
    restart: unless-stopped
    ports:
      - "8088:8088"
    environment:
      SUPERSET_SECRET_KEY: change-me-long-random-secret
    depends_on:
      - db
      - redis
```

### Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name bi.your-company.eu;

    location / {
        proxy_pass http://localhost:8088;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## Key Features

- SQL-based analytics
- Shared charts and dashboards
- Role-based access control
- Database connectors for many backends
- Fully self-hosted deployment

## Trade-offs

- Best for teams comfortable with data modeling
- Setup is more involved than a lightweight charting tool
- You still need a clean warehouse or reporting database

## Compliance Notes

- Keep source databases and dashboard storage inside EU-controlled infrastructure.
- Restrict access with SSO and role-based permissions.
- Restrict unnecessary outbound network access from Superset containers.
- As a self-hosted tool, you remain the data controller for reporting datasets.
- Ensure the `SUPERSET_SECRET_KEY` is kept secret and not committed to version control.

## EuroDesk Verdict

Apache Superset completes the business intelligence layer of a sovereign office stack by keeping analytics inside your own environment.
