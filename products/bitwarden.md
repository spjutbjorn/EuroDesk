# Bitwarden (Self-hosted)

**Category:** Password Manager
**Type:** Self-hosted (Vaultwarden)
**Jurisdiction:** EU-hostable when self-hosted
**Website:** [bitwarden.com](https://bitwarden.com) / [github.com/dani-garcia/vaultwarden](https://github.com/dani-garcia/vaultwarden)

## What It Is

Bitwarden is an open-source password manager with polished apps for every platform. When **self-hosted** using the official Bitwarden Server or the lightweight **Vaultwarden** (compatible third-party implementation), all your data stays on your EU infrastructure.

> **Note:** The managed cloud version of Bitwarden is hosted in the US. Only the self-hosted version qualifies for EuroDesk.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Bitwarden Unified or Vaultwarden on your own EU infrastructure |

## Which Server to Use

| Option | Description |
|---|---|
| **Bitwarden Unified** | Official self-hosted server (Docker, simpler than legacy) |
| **Vaultwarden** | Unofficial but widely used, very lightweight, single container |

This guide uses **Vaultwarden** for simplicity.

## Setup (Vaultwarden with Docker Compose)

### docker-compose.yml

```yaml
version: "3"

services:
  vaultwarden:
    image: vaultwarden/server:latest
    restart: unless-stopped
    volumes:
      - ./vw-data:/data
    ports:
      - "8084:80"
    environment:
      DOMAIN: "https://vault.your-company.eu"
      SIGNUPS_ALLOWED: "false"          # Disable public registration
      INVITATIONS_ALLOWED: "true"       # Allow admin to invite users
      ADMIN_TOKEN: "changeme-use-a-long-random-string"
      SMTP_HOST: "smtp.your-company.eu"
      SMTP_FROM: "vault@your-company.eu"
      SMTP_PORT: "587"
      SMTP_SECURITY: "starttls"
      SMTP_USERNAME: "vault@your-company.eu"
      SMTP_PASSWORD: "your-smtp-password"
      LOG_LEVEL: "warn"
      EXTENDED_LOGGING: "true"
```

### Generate Admin Token

```bash
openssl rand -base64 48
```

Replace `ADMIN_TOKEN` with the output.

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

Vaultwarden **requires HTTPS** (browsers block password manager APIs over HTTP):

```nginx
server {
    listen 443 ssl;
    server_name vault.your-company.eu;

    location / {
        proxy_pass http://localhost:8084;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
        proxy_read_timeout 90;
    }

    location /notifications/hub {
        proxy_pass http://localhost:8084;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

## Initial Setup

1. Navigate to `https://vault.your-company.eu/admin`
2. Enter your `ADMIN_TOKEN` to access the admin panel
3. **Invite users** from the admin panel (sends email with registration link)
4. Users create accounts and set their master password
5. **Admin panel** → **Organizations** → Create an organization for sharing

## User Setup (Client Side)

### Browser Extension

1. Install Bitwarden extension (Chrome, Firefox, Safari, Edge)
2. Click the extension icon → **Settings** → **Self-hosted environment**
3. Set Server URL: `https://vault.your-company.eu`
4. Log in with your account

### Desktop App

1. Download from [bitwarden.com/download](https://bitwarden.com/download)
2. **Settings** → **Server URL** → `https://vault.your-company.eu`
3. Log in

### Mobile App

Same process: Settings → Self-hosted → enter your server URL.

## Organizations (Team Sharing)

1. Create an **Organization** in the web vault
2. Invite team members to the organization
3. Create **Collections** (equivalent to folders) for grouping credentials
4. Share items to collections
5. Assign members to collections with **Can View** or **Can Edit** permissions

## Key Features

- End-to-end encryption with zero-knowledge architecture
- Browser extensions for all major browsers
- Desktop and mobile apps
- TOTP authenticator codes storage
- Secure notes and identity storage
- Password generator
- Breach monitoring (via Have I Been Pwned integration)
- Organizations for team sharing
- Two-step login (TOTP, email, FIDO2/WebAuthn)
- Vault health reports

## Backup

```bash
# Stop vaultwarden before backup to ensure consistency
docker compose stop vaultwarden
tar -czf vaultwarden-backup-$(date +%Y%m%d).tar.gz ./vw-data
docker compose start vaultwarden
```

Schedule this with a cron job:

```bash
0 2 * * * cd /opt/vaultwarden && docker compose stop vaultwarden && tar -czf /backups/vw-$(date +\%Y\%m\%d).tar.gz ./vw-data && docker compose start vaultwarden
```

## Compliance Notes

- **Sovereignty:** Bitwarden Inc. is a US company. While they offer an EU cloud region, it remains subject to the **US CLOUD Act**.
- **Self-hosting Advantage:** When self-hosted (Official or Vaultwarden) on your own EU infrastructure, Bitwarden Inc. has no access to your database or encryption keys. This effectively nullifies the reach of the CLOUD Act for your vault data.
- **Zero-knowledge:** Even in the cloud, all data is end-to-end encrypted. Bitwarden cannot decrypt your vault.
- **No Telemetry:** Self-hosted instances do not send vault metadata to US servers.
- **Audit:** Regular security audits of the Bitwarden protocol apply to both official and third-party implementations like Vaultwarden.

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Passbolt | GPG-based, excellent for teams; see separate guide |
| 1Password | US company, closed source |
| LastPass | US company, breached multiple times |
