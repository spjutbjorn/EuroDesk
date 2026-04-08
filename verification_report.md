# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all 61 tools in the `products/` directory for compliance with the EuroDesk Inclusion Rules.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Akeneo PIM** | Product Info Management | EU (France) | Self-hosted / SaaS |
| **Apache Superset** | BI / Dashboards | EU-hostable | Self-hosted |
| **AppFlowy** | Note-taking | US/Global (Exception) | Self-hosted (Exception) |
| **Bareos** | Backup / DR | Germany (EU) | Self-hosted |
| **BigBlueButton** | Webinars / E-Learning | Global (Exception) | Self-hosted |
| **Bitwarden (Self-hosted)** | Password Manager | EU-hostable | Self-hosted (Vaultwarden) |
| **Brevo** | Marketing | EU (France) | SaaS |
| **Cal.com** | Scheduling | US (Exception) | Self-hosted (Exception) |
| **Collabora Online** | Office Suite | Germany / UK (Adequacy) | Self-hosted or managed |
| **CryptPad** | Collaborative Docs (E2EE) | France (EU) | Self-hosted or managed |
| **DeepL** | Translation | Germany (EU) | Managed SaaS / API |
| **Documenso** | E-signing | Germany (EU) | Self-hosted or managed |
| **Easy!Appointments** | Scheduling | EU-hostable | Self-hosted |
| **Element / Matrix** | Team Communication | EU-hostable | Self-hosted or managed |
| **Excalidraw** | Whiteboarding | US/Global (Exception) | Self-hosted (Exception) |
| **Forgejo** | Git Hosting | EU-hostable | Self-hosted |
| **Framadate** | Scheduling | EU (France) | Self-hosted / Managed |
| **GLPI** | Asset Management | France (EU) | Self-hosted or managed |
| **Grafana + Loki** | Logging / Monitoring | EU-hostable (US OSS) | Self-hosted |
| **Jitsi Meet** | Video Conferencing | EU-hostable | Self-hosted or managed |
| **Kimai** | Time Tracking | EU (Germany) | Self-hosted / SaaS |
| **LimeSurvey** | Forms / Surveys | Germany (EU) | Self-hosted or managed |
| **Logseq** | Note-taking | Global (Exception) | Local-first Software |
| **Mailbox.org** | Email & Groupware | Germany (EU) | Managed SaaS |
| **MailerLite** | Marketing | EU (Lithuania / IE) | SaaS |
| **Matomo** | Web Analytics | EU (NZ Adequacy) | Self-hosted / SaaS |
| **Mattermost** | Team Messaging | EU-hostable | Self-hosted or managed |
| **Mullvad Browser** | Web Browser | EU (Sweden) | Local Software |
| **Mullvad VPN** | VPN | Sweden (EU) | Managed SaaS |
| **Nextcloud** | Storage & Collaboration | EU-hostable | Self-hosted or managed |
| **ONLYOFFICE** | Office Suite | EU-hostable (Latvia) | Self-hosted or managed |
| **Odoo** | ERP / CRM | Belgium (EU) | Self-hosted or managed |
| **OpenKM** | Document Workflow | Spain (EU) | Self-hosted or managed |
| **OpenOlat** | LMS | Switzerland (Adequacy) | Self-hosted or managed |
| **OpenProject** | Project Management | Germany (EU) | Self-hosted or managed |
| **Outline** | Team Wiki | EU-hostable | Self-hosted or managed |
| **Paperless-ngx** | Document Archiving | EU (Open Source) | Self-hosted |
| **Passbolt** | Password Manager | Luxembourg (EU) | Self-hosted or managed |
| **Penpot** | Design & Prototyping | Spain (EU) | Self-hosted or managed |
| **Personio** | HR & Recruitment | EU (Germany) | SaaS |
| **Planka** | Kanban Board | EU-hostable | Self-hosted |
| **Plausible Analytics** | Web Analytics | Estonia (EU) | Self-hosted or managed |
| **PrestaShop** | E-commerce | EU (France) | Self-hosted / Managed |
| **Proton Mail** | Email | Switzerland (Adequacy) | Managed SaaS |
| **Proton VPN** | VPN | Switzerland (Adequacy) | Managed SaaS |
| **Qwant** | Search Engine | France (EU) | Managed SaaS |
| **Recruitee** | HR & Recruitment | EU (Netherlands) | SaaS |
| **Sentry (Self-hosted)** | Error Tracking | EU-hostable | Self-hosted |
| **Shopware** | E-commerce | Germany (EU) | Self-hosted / SaaS |
| **Startpage** | Search Engine | Netherlands (EU) | Managed SaaS |
| **SwissTransfer** | File Transfer | Switzerland (Adequacy) | SaaS |
| **Tally** | Form Builder | Belgium (EU) | Managed SaaS |
| **Tresorit** | File Transfer | Switzerland (Adequacy) | SaaS |
| **Tuta** | Email | Germany (EU) | Managed SaaS |
| **Wazuh** | Security Monitoring | Spain (EU) | Self-hosted or managed |
| **Weblate** | Translation Mgmt | Czech Republic (EU) | Self-hosted or managed |
| **ZITADEL** | Identity / SSO | Switzerland (Adequacy) | Self-hosted or managed |
| **Zammad** | Helpdesk | Germany (EU) | Self-hosted or managed |
| **n8n** | Automation | Germany (EU) | Self-hosted or managed |
| **openrouteservice** | Routing / Fleet | Germany (EU) | Self-hosted or managed |
| **opsi** | Endpoint Management | Germany (EU) | Self-hosted |

## Key Compliance Observations

### 1. The Self-Hosting Exception (Rule 3)
A significant number of specialized tools (**AppFlowy, Logseq, Cal.com, Excalidraw, BigBlueButton**) are developed outside the EU but are included under the "Self-Hosting Exception." These tools are open-source and verified to allow full data residency on EU infrastructure, ensuring zero exposure to the US CLOUD Act.

### 2. Education and Learning (LMS)
The stack now includes formal e-learning and webinar tools (**OpenOlat, BigBlueButton**). These tools, originating from Switzerland and the global open-source community, provide a sovereign alternative for corporate training and academic institutions.

### 3. Localization and PIM
The inclusion of **Weblate** and **Akeneo PIM** ensures that cross-border EU businesses can manage translations and product information within European legal boundaries, preventing sensitive commercial data from leaking to US-based SaaS competitors.

### 4. Advanced Document Management
With **OpenKM** and **Paperless-ngx**, the stack now covers professional document workflow and archiving. This is critical for sectors like Finance and Legal that require strict record-keeping under EU regulations.
