# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all 40 tools in the `products/` directory for compliance with the EuroDesk Inclusion Rules.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Apache Superset** | BI / Dashboards | EU-hostable when self-hosted | Self-hosted |
| **Bareos** | Backup / Disaster Recovery | Germany (EU) via Bareos GmbH & Co. KG | Self-hosted |
| **Bitwarden (Self-hosted)** | Password Manager | EU-hostable when self-hosted | Self-hosted (Vaultwarden) |
| **Collabora Online** | Office Suite | Germany / United Kingdom (adequacy-approved) | Self-hosted or managed |
| **CryptPad** | Collaborative Documents (End-to-End Encrypted) | France (EU, GDPR) | Self-hosted or managed |
| **DeepL** | Translation | Germany (EU) | Managed SaaS / API |
| **Documenso** | E-signing | Germany (EU) | Self-hosted or managed |
| **Easy!Appointments** | Scheduling / Booking | EU-hostable when self-hosted | Self-hosted |
| **Element / Matrix** | Team Communication | EU-hostable (EU data centers) | Self-hosted or managed |
| **Forgejo** | Git Hosting, Code Review, Package Registry, CI/CD | EU-hostable (Community-governed) | Self-hosted |
| **GLPI** | Asset Management / CMDB | France (EU) via Teclib | Self-hosted or managed |
| **Grafana + Loki + Prometheus** | Logging, Monitoring & Alerting | EU-hostable (US-developed OSS) | Self-hosted |
| **Jitsi Meet** | Video Conferencing | EU-hostable | Self-hosted or managed |
| **LimeSurvey** | Forms / Surveys | Germany (EU) via LimeSurvey GmbH | Self-hosted or managed |
| **Mailbox.org** | Email & Groupware | Germany (EU, GDPR) | Managed SaaS |
| **Matomo** | Web Analytics | EU compliant (InnoCraft, NZ adequacy) | Self-hosted / SaaS |
| **Mattermost** | Team Messaging | EU-hostable (US-developed OSS) | Self-hosted or managed |
| **Mullvad Browser** | Web Browser | EU (Sweden) | Local Software |
| **Mullvad VPN** | VPN | Sweden (EU, GDPR) | Managed SaaS |
| **Nextcloud** | File Storage, Calendar, Contacts, Collaboration | EU-hostable | Self-hosted or managed |
| **ONLYOFFICE** | Office Suite / Document Editing | EU-hostable; Latvia (EU) | Self-hosted or managed |
| **Odoo** | CRM, Accounting / Invoicing, HR, Procurement | Belgium (EU) | Self-hosted or managed |
| **OpenProject** | Project Management | Germany (EU, GDPR) | Self-hosted or managed |
| **Outline** | Team Wiki & Knowledge Base | EU-hostable (US-developed OSS) | Self-hosted or managed |
| **Passbolt** | Team Password Manager | Luxembourg (EU, GDPR) | Self-hosted or managed |
| **Penpot** | Design & Prototyping | Spain (EU) | Self-hosted or managed |
| **Planka** | Kanban Board | EU-hostable (Community-governed) | Self-hosted |
| **Plausible Analytics** | Web Analytics | Estonia (EU) | Self-hosted or managed |
| **Proton Mail** | Email | Switzerland (Adequacy Decision) | Managed SaaS |
| **Proton VPN** | VPN | Switzerland (Adequacy Decision) | Managed SaaS |
| **Qwant** | Search Engine | France (EU, GDPR) | Managed SaaS |
| **Sentry (Self-hosted)** | Error Tracking & Application Monitoring | EU-hostable (US-developed OSS) | Self-hosted |
| **Startpage** | Search Engine | Netherlands (EU, GDPR) | Managed SaaS |
| **Tally** | Form Builder | Belgium (EU) | Managed SaaS |
| **Tuta (formerly Tutanota)** | Email | Germany (EU, GDPR) | Managed SaaS |
| **Wazuh** | Security Monitoring / Endpoint Security | Spain (EU) | Self-hosted or managed |
| **ZITADEL** | Identity / SSO | Switzerland (Adequacy Decision) | Self-hosted or managed |
| **Zammad** | Helpdesk / Ticketing | Germany (EU) | Self-hosted or managed |
| **n8n** | Automation / Workflows | Germany (EU) | Self-hosted or managed |
| **opsi** | Endpoint Management / MDM | Germany (EU) via uib GmbH | Self-hosted |

## Key Compliance Observations

### 1. Sovereignty and Self-Hosting
Tools with US-based developers (**Bitwarden, Grafana, Mattermost, Outline, Sentry, Apache Superset**) are strictly verified for **self-hosted** use only. Each of these guides contains specific instructions to disable telemetry and ensure data residency remains within EU infrastructure, satisfying Rule 3 of the Inclusion Rules.

### 2. EU-Native Managed Services
Many products in the stack (**DeepL, Tally, Tuta, Mailbox.org, Qwant, Startpage, Mullvad**) are EU-native companies offering managed SaaS that complies with Rule 2 by processing and storing data exclusively on EU-owned and operated infrastructure.

### 3. Swiss Adequacy
Switzerland-based tools (**Proton Mail, Proton VPN, ZITADEL**) are included under Rule 1, benefiting from the EU Commission's Adequacy Decision. These tools provide privacy protections equivalent to the GDPR and are immune to the US CLOUD Act.

### 4. Open Standards and No Lock-in
The stack prioritizes open-source software and open standards (e.g., **Matrix** for communication, **SVG** for design in Penpot, **LibreOffice** core in Collabora). This ensures that organizations can migrate between hosting providers or move to self-hosting without losing access to their data, satisfying the long-term sovereignty goals of EuroDesk.
