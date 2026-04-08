# EuroDesk Product Verification Report

**Date:** Wednesday, April 8, 2026
**Scope:** Verification of all 76 tools in the `products/` directory for compliance with the EuroDesk Inclusion Rules.

**Verification level:** Metadata and inclusion-rule audit based on official vendor or project sources. This report mirrors the current product metadata and pricing as of April 2026.

## Summary Verification Table

| Product | Category | Jurisdiction | Compliance Type |
| :--- | :--- | :--- | :--- |
| **Akeneo PIM** | Product Information Management (PIM) | EU (France) | Self-hosted / SaaS |
| **Aleph Alpha** | Industrial AI / LLM | Germany (EU) | Managed SaaS / API / Private Cloud |
| **AnythingLLM** | Private AI / Knowledge Base | EU-hostable (Open Source) | Self-hosted / Desktop App |
| **Apache Superset** | BI / Dashboards | EU-hostable when self-hosted | Self-hosted |
| **AppFlowy** | Note-taking & Workspaces | US/Global (Exception) | Self-hosted (Exception) |
| **Bareos** | Backup / Disaster Recovery | Germany (EU) via Bareos GmbH & Co. KG | Self-hosted |
| **BigBlueButton** | Webinars & E-Learning | Global (Exception) | Self-hosted |
| **Bitwarden (Self-hosted)** | Password Manager | EU-hostable when self-hosted | Self-hosted (Vaultwarden) |
| **Brevo** | Marketing & Newsletters | EU (France) | SaaS |
| **Cal.com** | Scheduling & Booking | US (Exception) | Self-hosted (Exception) / SaaS |
| **Collabora Online** | Office Suite | Germany / United Kingdom (adequacy-approved) | Self-hosted or managed |
| **CryptPad** | Collaborative Documents (End-to-End Encrypted) | France (EU, GDPR) | Self-hosted or managed |
| **Cryptomator** | Encryption / Data Protection | Germany (EU) | Local Software |
| **DeepL** | Translation | Germany (EU) | Managed SaaS / API |
| **Documenso** | E-signing | Germany (EU) | Self-hosted or managed |
| **EULLM** | AI Infrastructure, LLM Platform | EU-hostable | Self-hosted (open source) |
| **Easy!Appointments** | Scheduling / Booking | EU-hostable when self-hosted | Self-hosted |
| **Element / Matrix** | Team Communication | EU-hostable (servers in your chosen EU data center) | Self-hosted or managed |
| **Eramba** | Governance, Risk & Compliance (GRC) | Global (Exception) | Self-hosted |
| **Excalidraw** | Whiteboarding & Collaboration | US/Global (Exception) | Self-hosted (Exception) / SaaS |
| **Forgejo** | Git Hosting, Code Review, Package Registry, CI/CD | EU-hostable; community-governed open source | Self-hosted |
| **Framadate** | Scheduling & Booking | EU (France) | Self-hosted / Managed |
| **GLPI** | Asset Management / CMDB | France (EU) via Teclib | Self-hosted or managed |
| **GlobaLeaks** | Whistleblowing & Compliance | EU (Italy) | Self-hosted |
| **Grafana + Loki + Prometheus** | Logging, Monitoring & Alerting | EU-hostable; Grafana Labs is US-based | Self-hosted |
| **Jitsi Meet** | Video Conferencing | EU-hostable | Self-hosted or managed |
| **Kimai** | Time Tracking & Invoicing | EU (Germany) | Self-hosted / SaaS |
| **Langdock** | AI Assistant, Enterprise AI Platform | Germany (EU) | Managed SaaS / Own Cloud / On-Prem |
| **LimeSurvey** | Forms / Surveys | Germany (EU) via LimeSurvey GmbH | Self-hosted or managed |
| **Logseq** | Note-taking & Workspaces | Global (Exception) | Local-first Software |
| **Mailbox.org** | Email & Groupware | Germany (EU, GDPR) | Managed SaaS |
| **MailerLite** | Marketing & Newsletters | EU (Lithuania / Ireland) | SaaS |
| **Matomo** | Web Analytics | EU compliant (InnoCraft) | Self-hosted / SaaS |
| **Mattermost** | Team Messaging | EU-hostable | Self-hosted or managed (EU region) |
| **Mistral AI / Le Chat** | AI Assistant, LLM | France (EU) | Managed SaaS / Self-hosted / API |
| **Mixpost** | Social Media Management | EU (Czech Republic) | Self-hosted / SaaS |
| **Mullvad Browser** | Web Browser | EU (Sweden) | Local Software |
| **Mullvad VPN** | VPN | Sweden (EU, GDPR) | Managed SaaS |
| **Nextcloud** | File Storage, Calendar, Contacts, Collaboration | EU-hostable | Self-hosted or managed |
| **ONLYOFFICE** | Office Suite / Document Editing | EU-hostable; Latvia (EU) | Self-hosted or managed |
| **Odoo** | CRM, Accounting / Invoicing, HR, Procurement | Belgium (EU) | Self-hosted or managed |
| **Open WebUI** | AI Interface / LLM Frontend | EU-hostable (Open Source) | Self-hosted |
| **OpenKM** | Document Workflow / Records Management | Spain (EU) | Self-hosted or managed |
| **OpenOlat** | Learning Management System (LMS) | Switzerland (adequacy-approved) | Self-hosted or managed |
| **OpenProject** | Project Management | Germany (EU, GDPR) | Self-hosted or managed |
| **Outline** | Team Wiki & Knowledge Base | EU-hostable; Outline Inc. is US-based | Self-hosted or managed |
| **Paperless-ngx** | Document Management & Archiving | EU (Open Source) | Self-hosted |
| **Passbolt** | Team Password Manager | Luxembourg (EU, GDPR) | Self-hosted or managed |
| **Penpot** | Design & Prototyping | Spain (EU) | Self-hosted or managed |
| **Personio** | HR & Recruitment | EU (Germany) | SaaS |
| **Pimcore** | Digital Asset Management (DAM) & Master Data | EU (Austria) | Self-hosted / PaaS |
| **Planka** | Kanban Board | EU-hostable (open source, no vendor lock-in) | Self-hosted |
| **Plausible Analytics** | Web Analytics | Estonia (EU) | Self-hosted or managed |
| **PrestaShop** | E-commerce | EU (France) | Self-hosted / Managed |
| **Proton Mail** | Email | Switzerland (Adequacy Decision) | Managed SaaS |
| **Proton VPN** | VPN | Switzerland (Adequacy Decision) | Managed SaaS |
| **Qwant** | Search Engine | France (EU, GDPR) | Managed SaaS |
| **Recruitee** | HR & Recruitment | EU (Netherlands) | SaaS |
| **Sentry (Self-hosted)** | Error Tracking & Application Monitoring | EU-hostable when self-hosted | Self-hosted |
| **Shopware** | E-commerce | EU (Germany) | Self-hosted / SaaS |
| **Startpage** | Search Engine | Netherlands (EU, GDPR) | Managed SaaS |
| **Strapi** | Content Management System (Headless CMS) | EU (France) | Self-hosted / SaaS |
| **SwissTransfer** | File Transfer | Switzerland (Adequacy-Approved) | SaaS |
| **TYPO3** | Enterprise Content Management System (CMS) | EU (Switzerland/Germany) | Self-hosted |
| **Tally** | Form Builder | Belgium (EU) | Managed SaaS |
| **Tresorit** | File Transfer & Storage | Switzerland (Adequacy-Approved) | SaaS |
| **Tuta (formerly Tutanota)** | Email | Germany (EU, GDPR) | Managed SaaS |
| **VeraCrypt** | Encryption / Data Protection | France (EU) | Local Software |
| **Wazuh** | Security Monitoring / Endpoint Security | Spain (EU) | Self-hosted or managed |
| **Weblate** | Translation Management / Localization | Czech Republic (EU) | Self-hosted or managed |
| **ZITADEL** | Identity / SSO | Switzerland (Adequacy Decision) | Self-hosted or managed |
| **Zammad** | Helpdesk / Ticketing | Germany (EU) | Self-hosted or managed |
| **eustella** | AI Assistant | Austria (EU) | Managed SaaS (mobile-first) |
| **n8n** | Automation / Workflows | Germany (EU) | Self-hosted or managed |
| **openrouteservice** | Routing / Fleet Planning | Germany (EU) | Self-hosted or managed |
| **opsi** | Endpoint Management / MDM | Germany (EU) | Self-hosted |

## Key Compliance Observations

### 1. Sovereign AI and LLMs
The addition of **Mistral AI, Aleph Alpha, EULLM, Langdock, eustella, and Open WebUI** provides a complete, sovereign AI stack. These tools range from EU-native managed APIs (Mistral, Aleph Alpha) to fully self-hosted infrastructures (EULLM, developed in Italy under Apache 2.0) and frontends (Open WebUI), ensuring that "Generative AI" does not necessitate data export to non-EU jurisdictions.

**Maturity note:** eustella (Austria) is in closed beta as of April 2026 — not yet production-ready. EULLM is in early development. Both meet inclusion rules but should be flagged as evaluate-before-commit for migration planning. Langdock (Germany, ISO 27001, SOC 2 Type II) is the most enterprise-ready multi-model option, though its SaaS tier uses Azure Germany (US-owned infra) — on-prem deployment available for strict sovereignty.

### 2. The Self-Hosting Exception (Rule 3)
A significant number of specialized tools (**AppFlowy, Logseq, Cal.com, Excalidraw, BigBlueButton, AnythingLLM, Open WebUI, Eramba**) are developed outside the EU but are included under the "Self-Hosting Exception." These tools are open-source and verified to allow full data residency on EU infrastructure.

### 3. Specialization: PIM, CMS, and E-commerce
The inclusion of **Akeneo PIM, Shopware, PrestaShop, Strapi, and TYPO3** ensures that European digital presence and commercial infrastructure remain under EU legal protection, preventing sensitive customer and product data from leaking to US platforms.

### 4. Advanced Security & Governance
The stack now includes dedicated tools for **GRC (Eramba)**, **Whistleblowing (GlobaLeaks)**, and **Encryption (VeraCrypt, Cryptomator)**, providing a high-assurance environment for regulated sectors like Finance and Legal.
