# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all tools in the `products/` directory for EU rule and geographic compliance.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Bareos** | Backup / DR | Germany (EU) | Fully Self-hostable (EU-owned) |
| **Bitwarden** | Password Manager | EU-hostable | **Self-hosted only** (Vaultwarden) |
| **CryptPad** | Collaboration | France (EU) | Managed (Paris) or Self-hosted |
| **Documenso** | E-signing | Germany (EU) | Managed (EU) or Self-hosted |
| **Element** | Communication | EU-hostable | Managed (EU region) or Self-hosted |
| **Forgejo** | Git Hosting | EU-hostable | Community-governed (No US owner) |
| **Grafana/Loki** | Monitoring | EU-hostable | Self-hosted (Disable US telemetry) |
| **Jitsi Meet** | Video Calls | EU-hostable | Fully Self-hostable |
| **LimeSurvey** | Forms / Surveys | Germany (EU) | Managed (EU) or Self-hosted |
| **Mailbox.org** | Email | Germany (EU) | Managed (German data centers) |
| **Mattermost** | Communication | EU-hostable | Managed (EU region) or Self-hosted |
| **Mullvad VPN** | VPN | Sweden (EU) | Swedish jurisdiction |
| **Nextcloud** | Storage/Collab | EU-hostable | Managed (EU) or Self-hosted |
| **ONLYOFFICE** | Office Suite | Latvia (EU) | EU-developed; Self-hosted or Cloud |
| **OpenProject** | Project Mgmt | Germany (EU) | Managed (Germany) or Self-hosted |
| **opsi** | Endpoint Mgmt | Germany (EU) | Fully Self-hostable |
| **Outline** | Knowledge Base | EU-hostable | Managed (EU region) or Self-hosted |
| **Passbolt** | Password Manager | Luxembourg (EU) | Managed (EU) or Self-hosted |
| **Planka** | Kanban Board | EU-hostable | Open-source; Fully Self-hostable |
| **Proton (Mail/VPN)**| Email/VPN | Switzerland | Swiss FADP (EU Adequacy Decision) |
| **Qwant** | Search Engine | France (EU) | Independent French index |
| **Sentry** | Error Tracking | EU-hostable | **Self-hosted only** |
| **Startpage** | Search Engine | Netherlands (EU)| Amsterdam-based; EU Proxy |
| **Tuta** | Email | Germany (EU) | Hannover-based; German BDSG |
| **Zammad** | Helpdesk | Germany (EU) | Managed (EU) or Self-hosted |
| **ZITADEL** | Identity / SSO | Switzerland | Swiss FADP (EU Adequacy Decision) |

## Key Compliance Observations

### 1. The "Self-Hosted" Requirement
Several high-quality tools (**Bitwarden, Sentry, Outline**) are developed by US-based companies. Their managed "Cloud" versions are subject to US jurisdiction and data residency. To maintain compliance within the EuroDesk framework, these tools **MUST** be self-hosted on EU-owned infrastructure (e.g., Hetzner, OVHcloud) as detailed in their respective guides.

### 2. Swiss Adequacy (Proton, ZITADEL)
While Switzerland is not part of the EU/EEA, it maintains a formal "Adequacy Decision" from the European Commission. This means Swiss data protection laws (FADP) provide a level of protection equivalent to the GDPR, making **Proton** and **ZITADEL** products compatible with the privacy goals of this project.

### 3. Sovereign Infrastructure & Operations
New additions like **opsi** (Endpoint Management) and **Bareos** (Backup) are critical for professional office operations. These tools ensure that even the "low-level" management and recovery of systems remain under EU jurisdiction and open-source control. **Documenso** provides a key sovereign path for e-signing, which is often a legal bottleneck for companies relying on US SaaS.

### 4. Identity as the Core
**ZITADEL** fills the gap for modern, European-based identity management (SAML/OIDC). It serves as the bridge to integrate multiple "EuroDesk" tools into a single, secure Single Sign-On (SSO) experience without relying on Azure AD or Google Auth.
