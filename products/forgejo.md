# Forgejo

**Category:** Git Hosting, Code Review, Package Registry, CI/CD
**Type:** Self-hosted
**Jurisdiction:** EU-hostable; community-governed open source (no single corporate owner)
**Website:** [forgejo.org](https://forgejo.org)

## What It Is

Forgejo is a self-hosted Git platform — a GitHub alternative you run on your own EU server. It is a hard fork of Gitea, governed by the open-source community with no corporate control. It includes repositories, pull requests, issue tracking, a built-in package registry, and CI/CD via **Forgejo Actions** (GitHub Actions-compatible).

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Any EU VPS (Hetzner, OVHcloud, Scaleway) |
| **Codeberg.org** | Community-hosted Forgejo, servers in Germany — free for open source |

## Setup (Docker Compose)

### docker-compose.yml

```yaml
version: "3"

networks:
  forgejo:

volumes:
  forgejo_data:
  forgejo_db:

services:
  postgres:
    image: postgres:15-alpine
    restart: unless-stopped
    networks:
      - forgejo
    volumes:
      - forgejo_db:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: forgejo
      POSTGRES_USER: forgejo
      POSTGRES_PASSWORD: changeme

  forgejo:
    image: codeberg.org/forgejo/forgejo:7
    restart: unless-stopped
    networks:
      - forgejo
    depends_on:
      - postgres
    ports:
      - "3002:3000"
      - "2222:22"    # SSH git access
    volumes:
      - forgejo_data:/data
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    environment:
      USER_UID: 1000
      USER_GID: 1000
      FORGEJO__database__DB_TYPE: postgres
      FORGEJO__database__HOST: postgres:5432
      FORGEJO__database__NAME: forgejo
      FORGEJO__database__USER: forgejo
      FORGEJO__database__PASSWD: changeme
      FORGEJO__server__DOMAIN: git.your-company.eu
      FORGEJO__server__ROOT_URL: https://git.your-company.eu
      FORGEJO__server__SSH_DOMAIN: git.your-company.eu
      FORGEJO__server__SSH_PORT: 2222
      FORGEJO__service__DISABLE_REGISTRATION: "true"
      FORGEJO__service__REQUIRE_SIGNIN_VIEW: "true"
      FORGEJO__mailer__ENABLED: "true"
      FORGEJO__mailer__PROTOCOL: smtp+starttls
      FORGEJO__mailer__SMTP_ADDR: smtp.your-company.eu
      FORGEJO__mailer__SMTP_PORT: "587"
      FORGEJO__mailer__USER: git@your-company.eu
      FORGEJO__mailer__PASSWD: smtp-password
      FORGEJO__mailer__FROM: git@your-company.eu
```

### Start

```bash
docker compose up -d
```

### nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name git.your-company.eu;

    client_max_body_size 512M;

    location / {
        proxy_pass http://localhost:3002;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
    }
}
```

### SSH Git Access

For SSH clone/push, users connect on port `2222`:

```bash
git clone ssh://git@git.your-company.eu:2222/team/repo.git
```

Or add to `~/.ssh/config`:

```
Host git.your-company.eu
    Port 2222
    User git
```

Then use standard SSH URLs: `git@git.your-company.eu:team/repo.git`

## Initial Setup

1. Navigate to `https://git.your-company.eu`
2. Complete the installation wizard (settings are pre-filled from env vars)
3. Create the admin account
4. **Admin panel** → **Users** → invite team members

## Forgejo Actions (CI/CD)

Forgejo Actions is compatible with GitHub Actions workflows — you can reuse existing `.github/workflows/*.yml` files with minimal changes.

### Enable Actions

In `docker-compose.yml` add:

```yaml
      FORGEJO__actions__ENABLED: "true"
```

### Add a Runner

```yaml
  act-runner:
    image: code.forgejo.org/forgejo/act_runner:latest
    restart: unless-stopped
    networks:
      - forgejo
    depends_on:
      - forgejo
    volumes:
      - ./act_runner_data:/data
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      FORGEJO_INSTANCE_URL: http://forgejo:3000
      FORGEJO_RUNNER_REGISTRATION_TOKEN: "get-this-from-admin-panel"
```

Get the registration token from: **Admin Panel** → **Actions** → **Runners** → **Create new Runner**.

### Example Workflow

```yaml
# .forgejo/workflows/ci.yml
on: [push, pull_request]

jobs:
  test:
    runs-on: docker
    steps:
      - uses: actions/checkout@v3
      - name: Run tests
        run: npm test
      - name: Build
        run: npm run build
```

## Package Registry

Forgejo has a built-in package registry supporting:

| Type | Use Case |
|---|---|
| npm | JavaScript/Node.js packages |
| Maven | Java/JVM packages |
| PyPI | Python packages |
| Docker | Container images |
| Helm | Kubernetes charts |
| Generic | Any file/artifact |

Configure npm to use your Forgejo registry:

```bash
npm config set registry https://git.your-company.eu/api/packages/your-org/npm/
```

## Key Features

- Git repositories with web UI
- Pull requests and code review (inline comments, approvals)
- Issue tracker with labels, milestones, and boards
- Wiki per repository
- GitHub Actions-compatible CI/CD
- Built-in container and package registry
- Webhook support (integrates with Mattermost, etc.)
- Protected branches and required reviews
- LDAP/OAuth2 authentication
- Two-factor authentication
- API (GitHub-compatible)
- Mirror external repos (GitHub, GitLab)

## Backup

```bash
docker exec forgejo-forgejo-1 forgejo admin forgejo-dump -c /data/gitea/conf/app.ini
docker cp forgejo-forgejo-1:/data/forgejo-dump-*.zip ./backups/
```

## Compliance Notes

- Fully self-hosted on your EU infrastructure
- No telemetry (disable analytics in admin panel)
- All code and repository metadata stays on your servers
- Access log for audit trails
- Two-factor auth reduces unauthorized access risk
- GDPR: user data exportable and deletable via admin panel

## Alternatives Considered

| Alternative | Why not |
|---|---|
| GitHub | US company (Microsoft), data not EU-resident |
| GitLab.com | US company; self-hosted GitLab CE is a valid alternative (heavier) |
| Bitbucket | Atlassian, US company |
| Azure DevOps | Microsoft, US company |
