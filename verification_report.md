# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all tools in the `products/` directory for EU rule and geographic compliance.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Bitwarden** | Password Manager | EU-hostable | **Self-hosted only** (Vaultwarden) |
| **CryptPad** | Collaboration | France (EU) | Managed (Paris) or Self-hosted |
| **Element** | Communication | EU-hostable | Managed (EU region) or Self-hosted |
| **Forgejo** | Git Hosting | EU-hostable | Community-governed (No US owner) |
| **Grafana/Loki** | Monitoring | EU-hostable | Self-hosted (Disable US telemetry) |
| **Jitsi Meet** | Video Calls | EU-hostable | Fully Self-hostable |
| **Mailbox.org** | Email | Germany (EU) | Managed (German data centers) |
| **Mattermost** | Communication | EU-hostable | Managed (EU region) or Self-hosted |
| **Mullvad VPN** | VPN | Sweden (EU) | Swedish jurisdiction |
| **Nextcloud** | Storage/Collab | EU-hostable | Managed (EU) or Self-hosted |
| **ONLYOFFICE** | Office Suite | Latvia (EU) | EU-developed; Self-hosted or Cloud |
| **OpenProject** | Project Mgmt | Germany (EU) | Managed (Germany) or Self-hosted |
| **Outline** | Knowledge Base | EU-hostable | Managed (EU region) or Self-hosted |
| **Passbolt** | Password Manager | Luxembourg (EU) | Managed (EU) or Self-hosted |
| **Planka** | Kanban Board | EU-hostable | Open-source; Fully Self-hostable |
| **Proton (Mail/VPN)**| Email/VPN | Switzerland | Swiss FADP (EU Adequacy Decision) |
| **Qwant** | Search Engine | France (EU) | Independent French index |
| **Sentry** | Error Tracking | EU-hostable | **Self-hosted only** |
| **Startpage** | Search Engine | Netherlands (EU)| Amsterdam-based; EU Proxy |
| **Tuta** | Email | Germany (EU) | Hannover-based; German BDSG |

## Key Compliance Observations

### 1. The "Self-Hosted" Requirement
Several high-quality tools (**Bitwarden, Sentry, Outline**) are developed by US-based companies. Their managed "Cloud" versions are subject to US jurisdiction and data residency. To maintain compliance within the EuroDesk framework, these tools **MUST** be self-hosted on EU-owned infrastructure (e.g., Hetzner, OVHcloud) as detailed in their respective guides.

### 2. Swiss Adequacy (Proton)
While Switzerland is not part of the EU/EEA, it maintains a formal "Adequacy Decision" from the European Commission. This means Swiss data protection laws (FADP) provide a level of protection equivalent to the GDPR, making **Proton** products compatible with the privacy goals of this project.

### 3. Infrastructure Sovereignty
Compliance with GDPR (the rules) does not always guarantee sovereignty (the protection from foreign law). To prevent data access via the **US CLOUD Act**, it is critical to use providers whose parent companies are registered within the EU. The [hosting.md](air-file://krej1am36hlc78l8fp6n/Users/spjutbjorn/git/EuroDesk/products/hosting.md?type=file&root=%252F) guide identifies **Hetzner, OVHcloud, Scaleway, IONOS, STACKIT, UpCloud, Exoscale, and Open Telekom Cloud** as fully sovereign options.

### 4. Telemetry Configuration
For tools like **Grafana** and **Sentry**, the guides include specific environment variables (e.g., `SENTRY_BEACON=false`) to disable US-bound telemetry and ensure complete geographic data residency.
