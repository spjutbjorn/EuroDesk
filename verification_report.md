# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all 76 tools in the `products/` directory for consistency with the product documents currently stored in `products/`.  
**Verification level:** This report mirrors the current product metadata (`title`, `category`, `jurisdiction`, `type`) in the local product files. In this audit pass, selected higher-risk and newer entries — especially AI products and recently added tools — were additionally checked against official vendor or project sources. It still does not independently re-verify every pricing table or every installation command in every product guide.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Akeneo PIM** | Product Information Management (PIM) | EU (France) | Self-hosted / SaaS |
| **Aleph Alpha** | Industrial AI / LLM | Germany (EU) | Managed SaaS / API / Private Cloud |
| **AnythingLLM** | Private AI / Knowledge Base | EU-hostable (Open Source) | Self-hosted / Desktop App |
| **Apache Superset** | BI / Dashboards | EU-hostable when self-hosted | Self-hosted |
| **AppFlowy** | Note-taking & Workspaces | US/Global (Open Source / Self-Hosted Exception) | Self-hosted (Exception) |
| **Bareos** | Backup / Disaster Recovery | Germany (EU) via Bareos GmbH & Co. KG | Self-hosted |
| **BigBlueButton** | Webinars & E-Learning | Global (Open Source / Self-Hosted Exception) | Self-hosted |
| **Bitwarden (Self-hosted)** | Password Manager | EU-hostable when self-hosted | Self-hosted (Vaultwarden) |
| **Brevo** | Marketing & Newsletters | EU (France) | SaaS |
| **Cal.com** | Scheduling & Booking | US (Open Source / Self-Hosted Exception) | Self-hosted (Exception) / SaaS |
| **Collabora Online** | Office Suite | Germany / United Kingdom (adequacy-approved) | Self-hosted or managed |
| **Cryptomator** | Encryption / Data Protection | Germany (EU) | Local Software |
| **CryptPad** | Collaborative Documents (End-to-End Encrypted) | France (EU, GDPR) — flagship instance hosted by XWiki SAS, Paris | Self-hosted or managed |
| **DeepL** | Translation | Germany (EU) | Managed SaaS / API |
| **Documenso** | E-signing | Germany (EU) | Self-hosted or managed |
| **Easy!Appointments** | Scheduling / Booking | EU-hostable when self-hosted | Self-hosted |
| **Element / Matrix** | Team Communication | EU-hostable (servers in your chosen EU data center) | Self-hosted or managed |
| **Eramba** | Governance, Risk & Compliance (GRC) | Global (Open Source / Self-Hosted Exception) | Self-hosted |
| **EU Hosting Providers** | Cloud Infrastructure, GPU Hosting, AI Inference | EU-ägda bolag, data stannar i EU | IaaS / PaaS |
| **EULLM** | AI Infrastructure, LLM Platform | EU-hostable | Self-hosted (open source) |
| **eustella** | AI Assistant | Austria (EU) | Managed SaaS (mobile-first) |
| **Excalidraw** | Whiteboarding & Collaboration | US/Global (Open Source / Self-Hosted Exception) | Self-hosted (Exception) / SaaS |
| **Forgejo** | Git Hosting, Code Review, Package Registry, CI/CD | EU-hostable; community-governed open source (no single corporate owner) | Self-hosted |
| **Framadate** | Scheduling & Booking | EU (France) | Self-hosted / Managed |
| **GlobaLeaks** | Whistleblowing & Compliance | EU (Italy) | Self-hosted |
| **GLPI** | Asset Management / CMDB | France (EU) via Teclib | Self-hosted or managed |
| **Grafana + Loki + Prometheus** | Logging, Monitoring & Alerting | EU-hostable; Grafana Labs is US-based but the software is open source and fully self-hostable | Self-hosted |
| **Jitsi Meet** | Video Conferencing | EU-hostable | Self-hosted or managed |
| **Kimai** | Time Tracking & Invoicing | EU (Germany) | Self-hosted / SaaS |
| **Langdock** | AI Assistant, Enterprise AI Platform | Germany (EU) | Managed SaaS / Own Cloud / On-Prem |
| **LimeSurvey** | Forms / Surveys | Germany (EU) via LimeSurvey GmbH | Self-hosted or managed |
| **Logseq** | Note-taking & Workspaces | Global (Open Source / Self-Hosted Exception) | Local-first Software |
| **Mailbox.org** | Email & Groupware | Germany (EU, GDPR) | Managed SaaS |
| **MailerLite** | Marketing & Newsletters | EU (Lithuania / Ireland) | SaaS |
| **Matomo** | Web Analytics | EU compliant (InnoCraft) | Self-hosted / SaaS |
| **Mattermost** | Team Messaging | EU-hostable | Self-hosted or managed (EU region) |
| **Mistral AI / Le Chat** | AI Assistant, LLM | France (EU) | Managed SaaS / Self-hosted / API |
| **Mixpost** | Social Media Management | EU (Czech Republic) | Self-hosted / SaaS |
| **Mullvad Browser** | Web Browser | EU (Sweden) | Local Software |
| **Mullvad VPN** | VPN | Sweden (EU, GDPR) | Managed SaaS |
| **n8n** | Automation / Workflows | Germany (EU) | Self-hosted or managed |
| **Nextcloud** | File Storage, Calendar, Contacts, Collaboration | EU-hostable | Self-hosted or managed |
| **Odoo** | CRM, Accounting / Invoicing, HR, Procurement | Belgium (EU) | Self-hosted or managed |
| **ONLYOFFICE** | Office Suite / Document Editing | EU-hostable; ONLYOFFICE is developed by Ascensio System SIA (Latvia, EU) | Self-hosted or managed |
| **Open WebUI** | AI Interface / LLM Frontend | EU-hostable (Open Source) | Self-hosted |
| **OpenKM** | Document Workflow / Records Management | Spain (EU) | Self-hosted or managed |
| **OpenOlat** | Learning Management System (LMS) | Switzerland (adequacy-approved) | Self-hosted or managed |
| **OpenProject** | Project Management | Germany (EU, GDPR) — developed by OpenProject GmbH, Berlin | Self-hosted or managed |
| **openrouteservice** | Routing / Fleet Planning | Germany (EU) via HeiGIT / Heidelberg ecosystem | Self-hosted or managed |
| **opsi** | Endpoint Management / MDM | Germany (EU) via uib GmbH | Self-hosted |
| **Outline** | Team Wiki & Knowledge Base | EU-hostable; Outline Inc. is US-based but the software is fully self-hostable | Self-hosted or managed |
| **Paperless-ngx** | Document Management & Archiving | EU (Open Source) | Self-hosted |
| **Passbolt** | Team Password Manager | Luxembourg (EU, GDPR) — Passbolt SA, Luxembourg | Self-hosted or managed |
| **Penpot** | Design & Prototyping | Spain (EU) | Self-hosted or managed |
| **Personio** | HR & Recruitment | EU (Germany) | SaaS |
| **Pimcore** | Digital Asset Management (DAM) & Master Data | EU (Austria) | Self-hosted / PaaS |
| **Planka** | Kanban Board | EU-hostable (open source, no vendor lock-in) | Self-hosted |
| **Plausible Analytics** | Web Analytics | Estonia (EU) | Self-hosted or managed |
| **PrestaShop** | E-commerce | EU (France) | Self-hosted / Managed |
| **Proton Mail** | Email | Switzerland (equivalent EU protection, subject to Swiss FADP) | Managed SaaS |
| **Proton VPN** | VPN | Switzerland (equivalent EU protection, FADP) | Managed SaaS |
| **Qwant** | Search Engine | France (EU, GDPR) | Managed SaaS |
| **Recruitee** | HR & Recruitment | EU (Netherlands) | SaaS |
| **Sentry (Self-hosted)** | Error Tracking & Application Monitoring | EU-hostable when self-hosted; sentry.io managed is US-hosted | Self-hosted |
| **Shopware** | E-commerce | EU (Germany) | Self-hosted / SaaS |
| **Startpage** | Search Engine | Netherlands (EU, GDPR) | Managed SaaS |
| **Strapi** | Content Management System (Headless CMS) | EU (France) | Self-hosted / SaaS |
| **SwissTransfer** | File Transfer | Switzerland (Adequacy-Approved) | SaaS |
| **Tally** | Form Builder | Belgium (EU) | Managed SaaS |
| **Tresorit** | File Transfer & Storage | Switzerland (Adequacy-Approved) | SaaS |
| **Tuta (formerly Tutanota)** | Email | Germany (EU, GDPR) | Managed SaaS |
| **TYPO3** | Enterprise Content Management System (CMS) | EU (Switzerland/Germany) | Self-hosted |
| **Wazuh** | Security Monitoring / Endpoint Security | Spain (EU) | Self-hosted or managed |
| **Weblate** | Translation Management / Localization | Czech Republic (EU) | Self-hosted or managed |
| **Zammad** | Helpdesk / Ticketing | Germany (EU) | Self-hosted or managed |
| **ZITADEL** | Identity / SSO | Switzerland (GDPR-equivalent, strong privacy law) | Self-hosted or managed |

## Key Consistency Findings

### 1. The previous report was out of sync
The earlier version of this file did not fully match the current `products/` directory. It had:

- an outdated total count
- missing product entries
- shortened or normalized categories and jurisdictions that no longer matched the product documents exactly
- naming differences such as `Grafana + Loki` vs `Grafana + Loki + Prometheus`

### 2. This report now mirrors the product files exactly
Each row above is aligned to the corresponding product document’s:

- title
- category
- jurisdiction
- type

That makes this report suitable as a local consistency reference for the repository.

### 3. Local consistency does not guarantee external freshness
Some product documents may still require future source refreshes for:

- pricing
- hosting plan names
- setup commands
- legal wording on jurisdiction or compliance

Those checks should be done against official vendor or project documentation as a separate verification pass.

### 4. External corrections made in this audit pass
During this pass, clear source-based corrections were applied to:

- `products/openolat.md`
- `products/openkm.md`
- `products/aleph-alpha.md`
- `products/langdock.md`

These corrections addressed packaging / installation wording, hosting model precision, and outdated product positioning.
