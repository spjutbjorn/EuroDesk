# EuroDesk

A curated collection of EU-hosted (or EU-jurisdiction) tools for a fully productive office desk setup — no data leaving Europe.

## Principles

- **EU-hosted or EU-jurisdiction** — servers located in EU member states or countries with equivalent data protection (Switzerland, Norway, Iceland)
- **GDPR-compliant by design**
- **Self-hostable or managed** — each tool can run on EU infrastructure you control
- **Office-ready** — covers the full working day
- **Developer-ready** — Git, CI/CD, logging, error tracking, and docs included

## Tool Categories

### Communication
| Tool | Type | File |
|---|---|---|
| [Element / Matrix](products/element-matrix.md) | Team chat & messaging | `products/element-matrix.md` |
| [Jitsi Meet](products/jitsi-meet.md) | Video conferencing | `products/jitsi-meet.md` |
| [Mattermost](products/mattermost.md) | Team messaging | `products/mattermost.md` |

### Email
| Tool | Type | File |
|---|---|---|
| [Proton Mail](products/proton-mail.md) | Encrypted email | `products/proton-mail.md` |
| [Tuta](products/tuta.md) | Encrypted email | `products/tuta.md` |
| [Mailbox.org](products/mailbox-org.md) | Business email | `products/mailbox-org.md` |

### File Storage & Documents
| Tool | Type | File |
|---|---|---|
| [Nextcloud](products/nextcloud.md) | File sync, calendar, contacts | `products/nextcloud.md` |
| [Cryptpad](products/cryptpad.md) | Collaborative docs (E2E encrypted) | `products/cryptpad.md` |
| [ONLYOFFICE](products/onlyoffice.md) | Office suite | `products/onlyoffice.md` |

### Project Management
| Tool | Type | File |
|---|---|---|
| [OpenProject](products/openproject.md) | Project & task management | `products/openproject.md` |
| [Planka](products/planka.md) | Kanban board | `products/planka.md` |

### Password Management
| Tool | Type | File |
|---|---|---|
| [Passbolt](products/passbolt.md) | Team password manager | `products/passbolt.md` |
| [Bitwarden (self-hosted)](products/bitwarden.md) | Password manager | `products/bitwarden.md` |

### VPN
| Tool | Type | File |
|---|---|---|
| [Mullvad](products/mullvad.md) | VPN | `products/mullvad.md` |
| [Proton VPN](products/proton-vpn.md) | VPN | `products/proton-vpn.md` |

### Search
| Tool | Type | File |
|---|---|---|
| [Startpage](products/startpage.md) | Private search engine | `products/startpage.md` |
| [Qwant](products/qwant.md) | Private search engine | `products/qwant.md` |

### Developer Tools
| Tool | Type | File |
|---|---|---|
| [Forgejo](products/forgejo.md) | Git hosting, CI/CD, package registry | `products/forgejo.md` |
| [Sentry (self-hosted)](products/sentry.md) | Error tracking & crash reporting | `products/sentry.md` |
| [Grafana + Loki](products/grafana-loki.md) | Logging, metrics & alerting | `products/grafana-loki.md` |
| [Outline](products/outline.md) | Team wiki & knowledge base | `products/outline.md` |

## Quick Start

1. Start with **email** (Proton Mail or Tuta) — this is your identity anchor
2. Add **file storage** (Nextcloud) — replaces Google Drive / OneDrive
3. Set up **communication** (Element or Mattermost) — replaces Slack / Teams
4. Add **video** (Jitsi Meet) — replaces Zoom / Meet
5. Deploy a **password manager** (Passbolt or Bitwarden) — team-wide
6. Add a **VPN** (Mullvad or Proton VPN) for secure remote access

### Developer Quick Start

1. **Git hosting**: Forgejo — replaces GitHub/GitLab
2. **Wiki**: Outline — runbooks, ADRs, onboarding docs
3. **Error tracking**: Sentry (self-hosted) — replaces Datadog/Sentry.io
4. **Logging & monitoring**: Grafana + Loki + Prometheus — replaces Datadog/Splunk
