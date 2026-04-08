# OpenProject

**Category:** Project Management
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU, GDPR) — developed by OpenProject GmbH, Berlin
**Website:** [openproject.org](https://www.openproject.org)

## What It Is

OpenProject is the leading open-source project management software. It supports classic (Gantt/waterfall) and agile (Scrum/Kanban) methodologies. It replaces Jira, Asana, and Monday.com.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Any EU VPS |
| **OpenProject Enterprise Cloud (EU)** | Managed, hosted in Germany |
| **OpenProject on-premises** | Enterprise features + your own server |

## Plans (Cloud 2026)

| Plan | Price (User/Mo) | Min. Users | Key Features |
|---|---|---|---|
| **Basic** | €5.95 | 5 | Enterprise add-ons, basic support |
| **Professional** | €10.95 | 25 | SSO (SAML/OIDC), training |
| **Premium** | €15.95 | 100 | Premier support, remote hands |
| **Corporate** | Custom | High Vol | Custom plugins, dedicated engineer |

> **Community Edition:** Free for self-hosting. Includes core project management but lacks Enterprise add-ons (SSO, Two-Factor Auth, Branding).

## Setup (Self-hosted with Docker)

### docker-compose.yml

```yaml
version: "3.7"

networks:
  frontend:
  backend:

volumes:
  pgdata:
  opdata:
  tmp:

x-op-restart-policy: &restart_policy
  restart: unless-stopped

x-op-app: &app
  <<: *restart_policy
  image: openproject/openproject:14
  environment:
    OPENPROJECT_HOST__NAME: "project.your-company.eu"
    OPENPROJECT_HTTPS: "true"
    OPENPROJECT_DEFAULT__LANGUAGE: en
    OPENPROJECT_RAILS__CACHE__STORE: memcache
    OPENPROJECT_CACHE__MEMCACHE__SERVER: cache:11211
    OPENPROJECT_RAILS__RELATIVE__URL__ROOT: ""
    DATABASE_URL: "postgres://openproject:changeme@db/openproject?pool=20&encoding=unicode&reconnect=true"
    RAILS_MIN_THREADS: 4
    RAILS_MAX_THREADS: 16
    SECRET_KEY_BASE: "$(openssl rand -hex 64)"
    OPENPROJECT_SEED_ADMIN_USER_PASSWORD: "adminchangeme"
    OPENPROJECT_SEED_ADMIN_USER_PASSWORD_RESET: "false"

services:
  db:
    image: postgres:15
    <<: *restart_policy
    volumes:
      - pgdata:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: openproject
      POSTGRES_PASSWORD: changeme
      POSTGRES_DB: openproject
    networks:
      - backend

  cache:
    image: memcached
    <<: *restart_policy
    networks:
      - backend

  web:
    <<: *app
    command: "./docker/prod/web"
    ports:
      - "8082:8080"
    volumes:
      - opdata:/var/openproject/assets
      - tmp:/app/tmp
    networks:
      - frontend
      - backend
    depends_on:
      - db
      - cache

  worker:
    <<: *app
    command: "./docker/prod/worker"
    volumes:
      - opdata:/var/openproject/assets
      - tmp:/app/tmp
    networks:
      - backend
    depends_on:
      - db
      - cache
```

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name project.your-company.eu;

    location / {
        proxy_pass http://localhost:8082;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
    }
}
```

## Key Features

- **Work Packages**: Issues, tasks, bugs, features (Jira-like)
- **Gantt Charts**: Project timelines with dependencies
- **Agile Boards**: Scrum and Kanban boards
- **Backlogs**: Sprint planning
- **Time Tracking**: Log hours against work packages
- **Budgets**: Track project costs
- **Wikis**: Per-project documentation
- **Roadmaps**: Visual project roadmaps
- **Meetings**: Agenda and minutes management
- **GitHub/GitLab integration**: Link commits and PRs to work packages

## Initial Configuration

After first login:
1. **Administration** → **Users** → create accounts for your team
2. **Administration** → **Email** → configure SMTP (use your EU email server)
3. **Administration** → **Authentication** → configure SSO if needed
4. Create your first **Project** and invite team members

## LDAP / SSO Integration

```
Administration → Authentication → LDAP Authentication
```

Configure with your EU-hosted LDAP/Active Directory server.

## Compliance Notes

- OpenProject GmbH is incorporated in Berlin, Germany
- Self-hosted: all project data stays on your infrastructure
- Enterprise Edition includes GDPR-specific features
- Data Processing Agreement available from OpenProject GmbH
- Audit logging of all changes to work packages

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Jira | Atlassian is US company, data not EU-resident by default |
| Asana | US company |
| Monday.com | US company |
| Linear | US company |
