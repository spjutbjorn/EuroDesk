# ZITADEL

**Category:** Identity / SSO
**Type:** Self-hosted or managed
**Jurisdiction:** Switzerland (GDPR-equivalent, strong privacy law)
**Website:** [zitadel.com](https://zitadel.com)

## What It Is

ZITADEL is an identity and access management platform for single sign-on, user directories, MFA, passkeys, and machine-to-machine authentication. It can replace cloud identity providers for teams that want European jurisdiction and the option to self-host on EU infrastructure.

## EU Hosting Options

| Option | Description |
|---|---|
| **ZITADEL Cloud** | Managed service operated from Switzerland |
| **Self-hosted** | Run on your own EU Kubernetes or VM infrastructure |

## Good Fit For

- Single sign-on across internal apps
- Centralized user lifecycle management
- MFA, WebAuthn, and passkeys
- B2B or internal identity for office tools

## Self-Hosted Setup

### Requirements
- Linux server or Kubernetes cluster
- PostgreSQL
- Public domain for login flows

### Docker Compose Example

```yaml
version: "3.8"

services:
  postgres:
    image: postgres:16
    restart: unless-stopped
    environment:
      POSTGRES_DB: zitadel
      POSTGRES_USER: zitadel
      POSTGRES_PASSWORD: change-me
    volumes:
      - ./postgres:/var/lib/postgresql/data

  zitadel:
    image: ghcr.io/zitadel/zitadel:latest
    restart: unless-stopped
    command: start-from-init --masterkey "MasterkeyNeedsToHave32Characters!"
    environment:
      ZITADEL_DATABASE_POSTGRES_HOST: postgres
      ZITADEL_DATABASE_POSTGRES_PORT: 5432
      ZITADEL_DATABASE_POSTGRES_DATABASE: zitadel
      ZITADEL_DATABASE_POSTGRES_USER_USERNAME: zitadel
      ZITADEL_DATABASE_POSTGRES_USER_PASSWORD: change-me
      ZITADEL_EXTERNALSECURE: "true"
      ZITADEL_EXTERNALDOMAIN: sso.your-company.eu
      ZITADEL_EXTERNALPORT: 443
      ZITADEL_TLS_ENABLED: "false"
    ports:
      - "8085:8080"
    depends_on:
      - postgres
```

### Start

```bash
docker compose up -d
```

### Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name sso.your-company.eu;

    location / {
        proxy_pass http://localhost:8085;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## Recommended First Integrations

1. Protect your wiki and internal tools with SSO
2. Enable MFA for all admin users
3. Use SCIM or automated provisioning where possible
4. Add passkeys for phishing-resistant logins

## Key Features

- SAML, OpenID Connect, OAuth 2.0
- MFA, TOTP, WebAuthn, passkeys
- Organizations, roles, and delegated admin
- Machine users and API auth
- Self-hosted and managed options

## Trade-offs

- More infrastructure complexity than a simple local auth system
- Best suited for teams with multiple apps to integrate
- Kubernetes deployment is common for larger setups

## Compliance Notes

- **Jurisdiction:** CAOS AG, the company behind ZITADEL, is based in Switzerland.
- **Data Protection:** Switzerland has a formal "Adequacy Decision" from the European Commission, meaning its data protection laws (FADP) provide a level of protection equivalent to the GDPR.
- **Sovereignty:** Fully hostable on your own EU infrastructure. All identity data and login logs stay on your servers.
- **Privacy:** As an open-source tool, you control all identity metadata. No telemetry is sent to CAOS AG.
- **GDPR:** Fully compliant as a Swiss company.

## EuroDesk Verdict

If you want a European identity platform with both managed and self-hosted paths, ZITADEL is one of the strongest missing building blocks for a complete office stack.
