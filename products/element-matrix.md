# Element / Matrix

**Category:** Team Communication
**Type:** Self-hosted or managed
**Jurisdiction:** EU-hostable (servers in your chosen EU data center)
**Website:** [element.io](https://element.io) / [matrix.org](https://matrix.org)

## What It Is

Matrix is an open, decentralized communication protocol. Element is the most popular Matrix client. Together they provide Slack-like team messaging, direct messages, voice/video calls, and file sharing — with full federation and end-to-end encryption.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted (Synapse/Dendrite)** | Run your own Matrix homeserver on any EU VPS (Hetzner, Scaleway, OVHcloud) |
| **Element Cloud (EU region)** | Managed hosting with data in the EU |
| **Unify (element.io enterprise)** | Enterprise managed service, EU data residency available |

## Setup (Self-hosted with Synapse)

### Requirements
- A Linux server (Ubuntu 22.04 recommended)
- A domain name with DNS control
- PostgreSQL 14+

### Install Synapse

```bash
sudo apt install -y lsb-release wget apt-transport-https
sudo wget -O /usr/share/keyrings/matrix-org-archive-keyring.gpg https://packages.matrix.org/debian/matrix-org-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/matrix-org-archive-keyring.gpg] https://packages.matrix.org/debian/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/matrix-org.list
sudo apt update && sudo apt install matrix-synapse-py3
```

### Configure

Edit `/etc/matrix-synapse/homeserver.yaml`:

```yaml
server_name: "your-company.eu"
public_baseurl: "https://matrix.your-company.eu/"
database:
  name: psycopg2
  args:
    user: synapse
    password: your-db-password
    database: synapse
    host: localhost
enable_registration: false   # invite-only
```

### Reverse Proxy (nginx)

```nginx
server {
    listen 443 ssl;
    server_name matrix.your-company.eu;

    location / {
        proxy_pass http://localhost:8008;
        proxy_set_header X-Forwarded-For $remote_addr;
    }
}
```

### Start

```bash
sudo systemctl enable matrix-synapse
sudo systemctl start matrix-synapse
```

### Create Admin User

```bash
register_new_matrix_user -c /etc/matrix-synapse/homeserver.yaml http://localhost:8008
```

## Element Web Client

Deploy the Element web app alongside your homeserver:

```bash
# Download latest release
wget https://github.com/element-hq/element-web/releases/latest/download/element-vX.X.X.tar.gz
tar -xzf element-*.tar.gz -C /var/www/
cp /var/www/element-*/config.sample.json /var/www/element-*/config.json
```

Edit `config.json`:

```json
{
  "default_server_config": {
    "m.homeserver": {
      "base_url": "https://matrix.your-company.eu",
      "server_name": "your-company.eu"
    }
  }
}
```

## Key Features

- End-to-end encrypted channels and DMs
- Threads, reactions, file sharing
- Voice and video calls (via Element Call / Jitsi bridge)
- Bridges to Slack, Teams, IRC, WhatsApp
- Mobile apps (iOS, Android) and desktop apps

## Compliance Notes

- All data stays on your self-hosted server
- E2E encryption means even server admins cannot read messages
- Audit logging available for compliance
- GDPR: you control all user data and deletion

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Slack | US-hosted, data leaves EU |
| Microsoft Teams | US company, complex EU data residency setup |
| Discord | US-hosted, not suitable for business |
