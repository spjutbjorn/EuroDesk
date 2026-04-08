# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all 53 tools in the `products/` directory for compliance with the EuroDesk Inclusion Rules.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Apache Superset** | BI / Dashboards | EU-hostable when self-hosted | Self-hosted |
| **AppFlowy** | Note-taking & Workspaces | US/Global (Exception) | Self-hosted (Exception) |
| **Bareos** | Backup / Disaster Recovery | Germany (EU) | Self-hosted |
| **Bitwarden (Self-hosted)** | Password Manager | EU-hostable when self-hosted | Self-hosted (Vaultwarden) |
| **Brevo** | Marketing & Newsletters | EU (France) | SaaS |
| **Cal.com** | Scheduling & Booking | US (Exception) | Self-hosted (Exception) / SaaS |
| **Collabora Online** | Office Suite | Germany / UK (Adequacy-Approved) | Self-hosted or managed |
| **CryptPad** | Collaborative Documents (E2EE) | France (EU, GDPR) | Self-hosted or managed |
| **DeepL** | Translation | Germany (EU) | Managed SaaS / API |
| **Documenso** | E-signing | Germany (EU) | Self-hosted or managed |
| **Easy!Appointments** | Scheduling / Booking | EU-hostable when self-hosted | Self-hosted |
| **Element / Matrix** | Team Communication | EU-hostable (EU data centers) | Self-hosted or managed |
| **Forgejo** | Git Hosting, CI/CD | EU-hostable (Community-governed) | Self-hosted |
| **Framadate** | Scheduling & Booking | EU (France) | Self-hosted / Managed |
| **GLPI** | Asset Management / CMDB | France (EU) | Self-hosted or managed |
| **Grafana + Loki + Prometheus** | Logging & Monitoring | EU-hostable (US-developed OSS) | Self-hosted |
| **Jitsi Meet** | Video Conferencing | EU-hostable | Self-hosted or managed |
| **Kimai** | Time Tracking & Invoicing | EU (Germany) | Self-hosted / SaaS |
| **LimeSurvey** | Forms / Surveys | Germany (EU) | Self-hosted or managed |
| **Logseq** | Note-taking & Workspaces | Global (Exception) | Local-first Software |
| **Mailbox.org** | Email & Groupware | Germany (EU, GDPR) | Managed SaaS |
| **MailerLite** | Marketing & Newsletters | EU (Lithuania / Ireland) | SaaS |
| **Matomo** | Web Analytics | EU compliant (NZ adequacy) | Self-hosted / SaaS |
| **Mattermost** | Team Messaging | EU-hostable (US-developed OSS) | Self-hosted or managed |
| **Mullvad Browser** | Web Browser | EU (Sweden) | Local Software |
| **Mullvad VPN** | VPN | Sweden (EU, GDPR) | Managed SaaS |
| **Nextcloud** | File Storage & Collaboration | EU-hostable | Self-hosted or managed |
| **ONLYOFFICE** | Office Suite / Document Editing | EU-hostable; Latvia (EU) | Self-hosted or managed |
| **Odoo** | CRM, ERP & HR | Belgium (EU) | Self-hosted or managed |
| **OpenProject** | Project Management | Germany (EU, GDPR) | Self-hosted or managed |
| **Outline** | Team Wiki & Knowledge Base | EU-hostable (US-developed OSS) | Self-hosted or managed |
| **Passbolt** | Team Password Manager | Luxembourg (EU, GDPR) | Self-hosted or managed |
| **Penpot** | Design & Prototyping | Spain (EU) | Self-hosted or managed |
| **Personio** | HR & Recruitment | EU (Germany) | SaaS |
| **Planka** | Kanban Board | EU-hostable (Community-governed) | Self-hosted |
| **Plausible Analytics** | Web Analytics | Estonia (EU) | Self-hosted or managed |
| **PrestaShop** | E-commerce | EU (France) | Self-hosted / Managed |
| **Proton Mail** | Email | Switzerland (Adequacy Decision) | Managed SaaS |
| **Proton VPN** | VPN | Switzerland (Adequacy Decision) | Managed SaaS |
| **Qwant** | Search Engine | France (EU, GDPR) | Managed SaaS |
| **Recruitee** | HR & Recruitment | EU (Netherlands) | SaaS |
| **Sentry (Self-hosted)** | Error Tracking | EU-hostable (US-developed OSS) | Self-hosted |
| **Shopware** | E-commerce | EU (Germany) | Self-hosted / SaaS |
| **Startpage** | Search Engine | Netherlands (EU, GDPR) | Managed SaaS |
| **SwissTransfer** | File Transfer | Switzerland (Adequacy-Approved) | SaaS |
| **Tally** | Form Builder | Belgium (EU) | Managed SaaS |
| **Tresorit** | File Transfer & Storage | Switzerland (Adequacy-Approved) | SaaS |
| **Tuta (formerly Tutanota)** | Email | Germany (EU, GDPR) | Managed SaaS |
| **Wazuh** | Security Monitoring | Spain (EU) | Self-hosted or managed |
| **ZITADEL** | Identity / SSO | Switzerland (Adequacy Decision) | Self-hosted or managed |
| **Zammad** | Helpdesk / Ticketing | Germany (EU) | Self-hosted or managed |
| **n8n** | Automation / Workflows | Germany (EU) | Self-hosted or managed |
| **opsi** | Endpoint Management / MDM | Germany (EU) | Self-hosted |

## Key Compliance Observations

### 1. The Self-Hosting Exception (Rule 3)
Newly added tools developed outside the EU (**AppFlowy, Logseq, Cal.com**) have been verified under the "Self-Hosting Exception." These tools are open-source and allow full data residency on EU infrastructure when self-hosted, bypassing US cloud jurisdiction.

### 2. Marketing and E-commerce expansion
The stack now includes EU-native SaaS for marketing (**Brevo, MailerLite**) and e-commerce (**PrestaShop, Shopware**). These tools are critical for business growth while maintaining GDPR compliance and ensuring that customer data remains within the European data protection umbrella.

### 3. Specialized Business Ops (HR, Finance, Recruiting)
The inclusion of **Personio, Recruitee, and Kimai** marks a significant expansion into specialized business operations. These tools, originating from Germany and the Netherlands, ensure that sensitive HR and financial data are handled by EU-regulated entities.

### 4. Swiss Adequacy and Advanced Security
Swiss tools (**SwissTransfer, Tresorit, ZITADEL**) continue to provide high-security alternatives for file transfer and identity management, fully protected by the Swiss FADP and recognized by the EU for data adequacy.
