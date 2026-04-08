# Planka

**Category:** Kanban Board
**Type:** Self-hosted
**Jurisdiction:** EU-hostable (open source, no vendor lock-in)
**Website:** [planka.app](https://planka.app)

## What It Is

Planka is a lightweight, open-source Kanban board inspired by Trello. It is fully self-hosted, has a clean interface, and covers the day-to-day task management needs of small to medium teams without the complexity of full project management tools like OpenProject.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Planka on your own EU-owned infrastructure |

## Setup (Docker Compose — recommended)

### docker-compose.yml

```yaml
version: "3"

services:
  planka:
    image: ghcr.io/plankanban/planka:latest
    restart: unless-stopped
    volumes:
      - ./user-avatars:/app/public/user-avatars
      - ./project-background-images:/app/public/project-background-images
      - ./attachments:/app/private/attachments
    ports:
      - "3001:1337"
    environment:
      - BASE_URL=https://board.your-company.eu
      - TRUST_PROXY=0
      - DATABASE_URL=postgresql://planka:changeme@postgres/planka
      - SECRET_KEY_BASE=changeme-use-openssl-rand-hex-64
      - DEFAULT_ADMIN_EMAIL=admin@your-company.eu
      - DEFAULT_ADMIN_PASSWORD=changeme
      - DEFAULT_ADMIN_NAME=Admin
      - DEFAULT_ADMIN_USERNAME=admin
    depends_on:
      postgres:
        condition: service_healthy

  postgres:
    image: postgres:15-alpine
    restart: unless-stopped
    volumes:
      - ./db-data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: planka
      POSTGRES_USER: planka
      POSTGRES_PASSWORD: changeme
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U planka -d planka"]
      interval: 10s
      timeout: 5s
      retries: 5
```

### Generate a Secret Key

```bash
openssl rand -hex 64
```

Replace `changeme-use-openssl-rand-hex-64` with the output.

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name board.your-company.eu;

    location / {
        proxy_pass http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

## Plans (2026)

| Plan | Price (User/Mo) | Key Features |
|---|---|---|
| **Community** | $0 | Unlimited boards/users |
| **Pro** | ~€9.20 | Recurring cards, calendar, roles |
| **Installation**| €469 (one-time) | Professional server setup |

> **Note:** Planka Pro was introduced in 2025 to support the long-term development of the open-source core.

## Key Features

- Projects → Boards → Lists → Cards hierarchy
- Card labels, due dates, checklists, and attachments
- Card comments and activity log
- Member assignment per card
- Board backgrounds (colors and images)
- Drag-and-drop between lists
- Notifications (in-app)
- Simple user management

## Initial Setup

1. Navigate to `https://board.your-company.eu`
2. Log in with the admin credentials from `docker-compose.yml`
3. Create users: **Account** → **Administration** → **Add User**
4. Create your first project and board

## Backup

```bash
# Backup PostgreSQL
docker exec planka-postgres-1 pg_dump -U planka planka > planka-backup-$(date +%Y%m%d).sql

# Backup uploaded files
tar -czf planka-files-$(date +%Y%m%d).tar.gz ./user-avatars ./project-background-images ./attachments
```

## Limitations Compared to OpenProject

- No Gantt charts
- No time tracking
- No sprint/backlog management
- No milestone tracking
- Best for simple Kanban use cases; use OpenProject for complex projects

## Compliance Notes

- Fully self-hosted: no data leaves your server
- No telemetry or analytics
- Open source (AGPL-3.0)
- Minimal data collected: only what users explicitly enter

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Trello | Atlassian (US company) |
| Notion | US company |
| Wekan | Self-hosted alternative, but less actively maintained |
| Taiga | More feature-rich but heavier to operate |
