# Nextcloud

**Category:** File Storage, Calendar, Contacts, Collaboration
**Type:** Self-hosted or managed
**Jurisdiction:** EU-hostable
**Website:** [nextcloud.com](https://nextcloud.com)

## What It Is

Nextcloud is the most widely deployed self-hosted file sync and collaboration platform. It replaces Google Drive, Dropbox, Google Calendar, and Google Contacts. With apps like Nextcloud Office (powered by Collabora Online or ONLYOFFICE), it also handles document editing.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Any EU VPS (Hetzner, OVHcloud, Scaleway, Exoscale) |
| **Nextcloud GmbH Hosted** | Managed by Nextcloud, EU data centers |
| **IONOS Nextcloud** | Managed, German data centers |
| **Hetzner Storage Share** | Hetzner-managed Nextcloud, German/Finnish data centers |

## Setup (Self-hosted with Docker)

### Requirements
- Linux server with Docker and Docker Compose
- Domain name
- At least 2 GB RAM (4 GB recommended for office use)

### docker-compose.yml

```yaml
version: '3'

services:
  db:
    image: mariadb:10.11
    restart: always
    volumes:
      - db:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: changeme-root
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: nextcloud
      MYSQL_PASSWORD: changeme

  redis:
    image: redis:alpine
    restart: always

  nextcloud:
    image: nextcloud:stable
    restart: always
    ports:
      - "8080:80"
    depends_on:
      - db
      - redis
    volumes:
      - nextcloud:/var/www/html
      - ./data:/var/www/html/data
    environment:
      MYSQL_HOST: db
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: nextcloud
      MYSQL_PASSWORD: changeme
      REDIS_HOST: redis
      NEXTCLOUD_ADMIN_USER: admin
      NEXTCLOUD_ADMIN_PASSWORD: changeme-admin
      NEXTCLOUD_TRUSTED_DOMAINS: files.your-company.eu
      OVERWRITEPROTOCOL: https

volumes:
  db:
  nextcloud:
```

### Start

```bash
docker compose up -d
```

### Reverse Proxy (nginx)

```nginx
server {
    listen 443 ssl;
    server_name files.your-company.eu;

    client_max_body_size 512M;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
        proxy_read_timeout 86400;
    }
}
```

## Enable Office Document Editing

### Option A: Collabora Online (built-in CODE)

In Nextcloud admin panel:
1. **Apps** → Search "Nextcloud Office" → Enable
2. **Settings** → **Nextcloud Office** → Use Built-in CODE server
3. Done — `.docx`, `.xlsx`, `.pptx` files open in-browser

### Option B: ONLYOFFICE (separate container)

```yaml
  onlyoffice:
    image: onlyoffice/documentserver:latest
    restart: always
    ports:
      - "8081:80"
```

Then in Nextcloud: **Apps** → Install ONLYOFFICE connector → Configure with `http://onlyoffice`.

## Recommended Apps to Enable

| App | Purpose |
|---|---|
| **Nextcloud Office** | Document editing |
| **Calendar** | Team calendars (CalDAV) |
| **Contacts** | Address book (CardDAV) |
| **Talk** | Audio/video calls and chat |
| **Mail** | Email client (IMAP) |
| **Tasks** | To-do lists |
| **Deck** | Kanban boards |
| **Notes** | Markdown notes |
| **Forms** | Surveys and forms |
| **Recognize** | AI-powered photo recognition |

## Key Features

- File sync clients for Windows, macOS, Linux, iOS, Android
- Real-time collaborative document editing
- Shared team folders
- External storage (SFTP, S3) integration
- WebDAV access
- Audit logging

## Maintenance

```bash
# Run OCC commands inside the container
docker exec --user www-data nextcloud-nextcloud-1 php occ status
docker exec --user www-data nextcloud-nextcloud-1 php occ upgrade

# Update container
docker compose pull && docker compose up -d
```

## Compliance Notes

- All data on your infrastructure
- Built-in audit log and file access log
- GDPR-compliant user data export and deletion (via OCC commands)
- Data Processing Agreement available from Nextcloud GmbH
- End-to-end encryption app available for sensitive folders

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Google Drive | US company, US jurisdiction |
| Dropbox | US company |
| OneDrive / SharePoint | US company, EU residency requires M365 EU add-on |
