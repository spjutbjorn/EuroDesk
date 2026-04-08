# Passbolt

**Category:** Team Password Manager
**Type:** Self-hosted or managed
**Jurisdiction:** Luxembourg (EU, GDPR) — Passbolt SA, Luxembourg
**Website:** [passbolt.com](https://www.passbolt.com)

## What It Is

Passbolt is an open-source, end-to-end encrypted password manager designed for teams. It allows sharing credentials securely among team members, with full audit trails and role-based access control.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted (Community)** | Free, unlimited users, on your EU server |
| **Passbolt Cloud (EU)** | Managed, EU data centers |
| **Passbolt Pro (self-hosted)** | Paid features + self-hosted |

## Plans

| Plan | Type | Price |
|---|---|---|
| **Community** | Self-hosted | Free |
| **Pro (self-hosted)** | Self-hosted | 48 €/user/year |
| **Cloud** | Managed SaaS | 48 €/user/year |
| **Business** | Managed SaaS | Custom |

## Setup (Self-hosted with Docker)

### Requirements
- Docker and Docker Compose
- A domain name with SSL
- An SMTP server for email invitations

### docker-compose.yml

```yaml
version: "3.9"

services:
  db:
    image: mariadb:10.11
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: changeme-root
      MYSQL_DATABASE: passbolt
      MYSQL_USER: passbolt
      MYSQL_PASSWORD: changeme
    volumes:
      - database_volume:/var/lib/mysql

  passbolt:
    image: passbolt/passbolt:latest-ce
    restart: unless-stopped
    depends_on:
      - db
    environment:
      APP_FULL_BASE_URL: https://pass.your-company.eu
      DATASOURCES_DEFAULT_HOST: db
      DATASOURCES_DEFAULT_USERNAME: passbolt
      DATASOURCES_DEFAULT_PASSWORD: changeme
      DATASOURCES_DEFAULT_DATABASE: passbolt
      EMAIL_DEFAULT_FROM: no-reply@your-company.eu
      EMAIL_TRANSPORT_DEFAULT_HOST: smtp.your-company.eu
      EMAIL_TRANSPORT_DEFAULT_PORT: 587
      EMAIL_TRANSPORT_DEFAULT_USERNAME: smtp-user@your-company.eu
      EMAIL_TRANSPORT_DEFAULT_PASSWORD: smtp-password
      EMAIL_TRANSPORT_DEFAULT_TLS: "true"
    volumes:
      - gpg_volume:/etc/passbolt/gpg
      - jwt_volume:/etc/passbolt/jwt
    command: ["/usr/bin/wait-for.sh", "-t", "0", "db:3306", "--", "/docker-entrypoint.sh"]
    ports:
      - "8083:80"
      - "8443:443"

volumes:
  database_volume:
  gpg_volume:
  jwt_volume:
```

### Start

```bash
docker compose up -d
```

### Create Admin User

```bash
docker exec passbolt-passbolt-1 su -m -c "/usr/share/php/passbolt/bin/cake passbolt register_user -u admin@your-company.eu -f Admin -l User -r admin" -s /bin/sh www-data
```

Follow the link in the output to complete admin setup in your browser.

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name pass.your-company.eu;

    location / {
        proxy_pass https://localhost:8443;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_ssl_verify off;
    }
}
```

## Browser Extension Setup (Per User)

1. Install the Passbolt browser extension (Chrome, Firefox, Edge, Brave)
2. Navigate to `https://pass.your-company.eu`
3. Click your invite link (sent by email)
4. Generate your personal GPG key pair
5. Set your passphrase — **this is never sent to the server**

## Key Features

- End-to-end GPG encryption for all passwords
- Shared folders and teams
- Role-based access: Owner, Manager, Can Edit, Can Read
- One-click password copy/fill via browser extension
- Password generator
- Audit log: see who accessed what and when
- TOTP/MFA secrets management (Pro)
- Slack/Teams notifications (Pro)
- Directory sync (LDAP/AD) (Pro)
- Mobile apps (iOS, Android)

## Sharing Passwords with a Team

1. Create a **Group** (e.g., "DevOps", "Finance")
2. Add team members to the group
3. Share a password with the group: **Password** → **Share** → select group
4. Sharing is E2E encrypted — Passbolt server never sees plaintext

## Compliance Notes

- Passbolt SA is registered in Luxembourg (EU)
- Zero-knowledge architecture: server stores only GPG-encrypted ciphertext
- Full audit trail for compliance
- GDPR-compliant by design
- Open source (AGPL-3.0)
- Data Processing Agreement available

## Alternatives Considered

| Alternative | Why not |
|---|---|
| 1Password | US company, closed source |
| LastPass | US company, history of breaches |
| Dashlane | US company |
| Bitwarden | US company (see separate self-hosted Bitwarden guide) |
