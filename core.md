# EuroDesk Core Product Mapping

This document maps the EuroDesk sovereign office stack to the most common white-collar roles. To maintain efficiency and privacy, each role starts with a "Universal Base Stack" and adds only the essential specialized tools required for their daily operations.

## 0. Universal Base Stack (Mandatory for All)
*The essential foundation for any sovereign office workstation.*
*   **Email & Productivity:** [Proton Mail](products/proton-mail.md), [Tuta](products/tuta.md), or [Mailbox.org](products/mailbox-org.md).
*   **Chat & Collaboration:** [Element](products/element-matrix.md), [Mattermost](products/mattermost.md), and [Jitsi Meet](products/jitsi-meet.md).
*   **File Storage & Editing:** [Nextcloud](products/nextcloud.md) with [ONLYOFFICE](products/onlyoffice.md) or [Collabora Online](products/collabora.md).
*   **Security & Browsing:** [Passbolt](products/passbolt.md), [Mullvad VPN](products/mullvad.md), and [Mullvad Browser](products/mullvad-browser.md).
*   **AI Assistant:** [Mistral AI](products/mistral.md) (Managed or Self-hosted assistant).
*   **Search:** [Startpage](products/startpage.md) or [Qwant](products/qwant.md).

---

## 1. Role-Specific Core Add-ons

### 💼 Administration & Office Support
*   [Easy!Appointments](products/easyappointments.md) (Scheduling & Meeting Slots)
*   [Documenso](products/documenso.md) (Electronic Signatures for approvals)
*   [CryptPad](products/cryptpad.md) (Secure, end-to-end encrypted temporary documents)
*   [Paperless-ngx](products/paperless-ngx.md) (Automated document archiving and OCR for physical mail)
*   [Mistral AI](products/mistral.md) (Drafting emails and summarizing meeting notes)

### 📈 Management & Leadership
*   [OpenProject](products/openproject.md) (Timelines, Gantt charts, and resource planning)
*   [Planka](products/planka.md) (Team-level Kanban boards)
*   [n8n](products/n8n.md) (Workflow automation between departments)
*   [Excalidraw](products/excalidraw.md) (Collaborative whiteboarding for planning sessions)
*   [Mistral AI](products/mistral.md) (Strategic analysis and reporting summaries)

### ⚖️ Business, Finance & Legal
*   [Odoo](products/odoo.md) (Full accounting, VAT, and invoicing engine)
*   [Documenso](products/documenso.md) (Contract signing and tracking)
*   [SwissTransfer](products/swisstransfer.md) (Secure, large file transfers for sensitive documents)
*   [Paperless-ngx](products/paperless-ngx.md) (Digital records management and audit-ready archiving)
*   [Aleph Alpha](products/aleph-alpha.md) (Legal document analysis and verifiable AI reasoning)
*   [AnythingLLM](products/anything-llm.md) (Private RAG across large contract and case law volumes)

### 📣 Sales, Marketing & Communication
*   [Odoo](products/odoo.md) (CRM & Lead Management)
*   [Brevo](products/brevo.md) or [MailerLite](products/mailerlite.md) (Compliant Newsletters & Campaigns)
*   [Matomo](products/matomo.md) (Marketing and web analytics)
*   [Tally](products/tally.md) (Simple form building for lead acquisition)
*   [Akeneo PIM](products/akeneo.md) (Centralized product information for marketing channels)

### 👥 Human Resources (HR)
*   [Personio](products/personio.md) (Employee lifecycle and records management)
*   [Recruitee](products/recruitee.md) (Applicant tracking and hiring pipelines)
*   [Odoo](products/odoo.md) (Payroll and expense management)
*   [Paperless-ngx](products/paperless-ngx.md) (Secure archiving of personnel files and contracts)

### 💻 Information Technology (IT) & Data
*   [Forgejo](products/forgejo.md) (Git hosting, CI/CD, and package registry)
*   [ZITADEL](products/zitadel.md) (Identity Management & Single Sign-On across the stack)
*   [Grafana + Loki](products/grafana-loki.md) (System-wide observability and logging)
*   [Wazuh](products/wazuh.md) (Security monitoring and vulnerability detection)
*   [opsi](products/opsi.md) (Automated software deployment for endpoints)
*   [Excalidraw](products/excalidraw.md) (System architecture and flow diagramming)
*   [Open WebUI](products/open-webui.md) (Sovereign frontend for technical AI tasks)
*   [EULLM](products/eullm.md) (Self-hosted model serving and registry)

### 🛠️ Customer Success & Support
*   [Zammad](products/zammad.md) (Helpdesk, ticket management, and service desk)
*   [n8n](products/n8n.md) (Automating support-to-engineering escalations)
*   [Akeneo PIM](products/akeneo.md) (Accurate product data for troubleshooting)
*   [Mistral AI](products/mistral.md) (Automated response drafting and sentiment analysis)

### 🎨 Creative & Design Services
*   [Penpot](products/penpot.md) (Design, prototyping, and SVG-based UI/UX)
*   [Outline](products/outline.md) (Design system documentation and knowledge base)
*   [Excalidraw](products/excalidraw.md) (Low-fidelity wireframing and sketching)
*   [Mistral AI](products/mistral.md) (Creative brainstorming and copy drafting)

### 🏗️ Specialized (Consulting & Engineering)
*   [GLPI](products/glpi.md) (IT asset and hardware management)
*   [Bareos](products/bareos.md) (Disaster recovery and backup for technical projects)
*   [DeepL](products/deepl.md) (High-accuracy translation for technical consulting)
*   [Excalidraw](products/excalidraw.md) (Technical diagramming and brainstorming)
*   [AnythingLLM](products/anything-llm.md) (Deep technical RAG for expert-level queries)

### 🔬 Research, Development & Innovation (RDI)
*   [Logseq](products/logseq.md) or [AppFlowy](products/appflowy.md) (Personal/Team knowledge graphing)
*   [Forgejo](products/forgejo.md) (IP/Code repository)
*   [Excalidraw](products/excalidraw.md) (Visualizing research concepts and hypotheses)
*   [EULLM](products/eullm.md) (Running experimental or domain-specific models locally)
*   [AnythingLLM](products/anything-llm.md) (Corpus-based analysis of academic/technical literature)

### 🏛️ Public Administration & Government
*   [LimeSurvey](products/limesurvey.md) (Formal citizen feedback and research surveys)
*   [Documenso](products/documenso.md) (Official decision and permit signing)
*   [OpenKM](products/openkm.md) (Structured records, approvals, and retention workflows)
*   [Paperless-ngx](products/paperless-ngx.md) (Mass-digitization of public records)
*   [Aleph Alpha](products/aleph-alpha.md) (Verifiable AI for policy analysis and administrative decisions)

### 📦 Procurement & Supply Chain
*   [Odoo](products/odoo.md) (Inventory, warehouse, and purchasing management)
*   [GLPI](products/glpi.md) (Supplier and maintenance contract tracking)
*   [Akeneo PIM](products/akeneo.md) (Managing supplier technical data and catalogs)

### 🎓 Education & Training
*   [Tally](products/tally.md) (Online tests, registration, and student feedback)
*   [Jitsi Meet](products/jitsi-meet.md) (Classroom-style video delivery)
*   [OpenOlat](products/openolat.md) (Full LMS for courses, assessments, and learner administration)
*   [BigBlueButton](products/bigbluebutton.md) (Advanced virtual classroom with whiteboards and polls)

### 🌍 Non-Profit & NGO Operations
*   [LimeSurvey](products/limesurvey.md) (Project outcome and donor reporting)
*   [CryptPad](products/cryptpad.md) (High-sensitivity advocacy and policy documentation)
*   [Paperless-ngx](products/paperless-ngx.md) (Donor agreement and grant archiving)

### 🏥 Healthcare Admin
*   [ZITADEL](products/zitadel.md) (Strict patient data access control and identity)
*   [Documenso](products/documenso.md) (Medical consent and administrative signing)
*   [Paperless-ngx](products/paperless-ngx.md) (Archiving of non-clinical records and insurance forms)

### 🚀 Product, Strategy & Business Operations
*   [Apache Superset](products/apache-superset.md) (BI Dashboards and strategic metrics)
*   [n8n](products/n8n.md) (Operational process automation)
*   [OpenProject](products/openproject.md) (Roadmap and strategic execution)
*   [Excalidraw](products/excalidraw.md) (Strategy mapping and workshop whiteboarding)

### 🏦 Banking, Insurance & Finance
*   [Wazuh](products/wazuh.md) (Regulatory compliance monitoring and audit logging)
*   [ZITADEL](products/zitadel.md) (Customer-facing identity and high-assurance auth)
*   [Paperless-ngx](products/paperless-ngx.md) (Regulatory-grade archiving of transaction records)

### 🏠 Real Estate & Facilities
*   [GLPI](products/glpi.md) (Building maintenance and facility asset tracking)
*   [Odoo](products/odoo.md) (Lease billing and financial contracts)
*   [Paperless-ngx](products/paperless-ngx.md) (Property deed and lease agreement archiving)

### 📰 Media, Publishing & Editorial
*   [Collabora Online](products/collabora.md) (Fine-grained document track-changes and review)
*   [Outline](products/outline.md) (Knowledge base and internal editorial guides)
*   [Weblate](products/weblate.md) (Multilingual publishing and localization workflows)
*   [Paperless-ngx](products/paperless-ngx.md) (Press release and media asset archiving)

### 🚛 Logistics, Transportation & Fleet Management
*   [Odoo](products/odoo.md) (Inventory, shipping, and routing management)
*   [GLPI](products/glpi.md) (Fleet, vehicle, and asset tracking)
*   [n8n](products/n8n.md) (Automating tracking and dispatch notifications)
*   [openrouteservice](products/openrouteservice.md) (Route calculation, matrices, and spatial planning)
*   [Paperless-ngx](products/paperless-ngx.md) (Waybill and customs document archiving)

### 🏨 Hospitality, Tourism & Travel Management
*   [Odoo](products/odoo.md) (POS, bookings, and customer billing)
*   [Easy!Appointments](products/easyappointments.md) (Service and slot-based bookings)
*   [n8n](products/n8n.md) (Connecting booking engines to internal systems)
*   [Paperless-ngx](products/paperless-ngx.md) (Invoice and vendor agreement archiving)

### ⚡ Energy, Utilities & Environmental Services
*   [Apache Superset](products/apache-superset.md) (Grid and energy market visualizations)
*   [Wazuh](products/wazuh.md) (Operational monitoring of critical management systems)
*   [Odoo](products/odoo.md) (Project and maintenance management)
*   [Paperless-ngx](products/paperless-ngx.md) (Archiving of maintenance logs and environmental reports)

### 🛍️ Retail & E-commerce Operations
*   [PrestaShop](products/prestashop.md) or [Shopware](products/shopware.md) (European-native e-commerce engines)
*   [Odoo](products/odoo.md) (Omnichannel retail inventory and POS)
*   [Matomo](products/matomo.md) (Privacy-compliant conversion and sales analytics)
*   [Akeneo PIM](products/akeneo.md) (Managing high-volume product catalogs and metadata)

### 🖼️ Arts, Culture & Museum Management
*   [GLPI](products/glpi.md) (Collection management and artifact tracking)
*   [Nextcloud](products/nextcloud.md) (High-resolution asset storage and sharing)
*   [CryptPad](products/cryptpad.md) (Collaborative planning for sensitive exhibitions)
*   [Paperless-ngx](products/paperless-ngx.md) (Archiving of loan agreements and provenance records)

### 🌍 Translation, Interpretation & Localization
*   [DeepL](products/deepl.md) (Professional-grade AI translation and API)
*   [Nextcloud](products/nextcloud.md) (Secure file exchange for large translation projects)
*   [Outline](products/outline.md) (Terminology management and shared glossaries)
*   [Weblate](products/weblate.md) (Translation memory, glossary, and review workflows)

### 📐 Architecture, Urban Planning & Construction Management
*   [Nextcloud](products/nextcloud.md) (Large-scale document and CAD/BIM model management)
*   [OpenProject](products/openproject.md) (Complex construction timelines and project tasks)
*   [Documenso](products/documenso.md) (Signing of technical approvals and site plans)
*   [openrouteservice](products/openrouteservice.md) (Spatial route analysis and territory planning)
*   [Excalidraw](products/excalidraw.md) (Concept sketching and site layout planning)

### 🛡️ Safety, Quality & Regulatory Compliance (QHSE)
*   [Wazuh](products/wazuh.md) (Audit trails, file integrity, and security monitoring)
*   [ZITADEL](products/zitadel.md) (Identity governance and high-assurance access controls)
*   [Odoo](products/odoo.md) (Quality control, audit logs, and non-conformance tracking)
*   [Paperless-ngx](products/paperless-ngx.md) (Strict version control and archiving of SOPs and compliance forms)

### ⚖️ Legal Practice & Law Firms
*   [OpenKM](products/openkm.md) (Case files, document workflows, and records control)
*   [Documenso](products/documenso.md) (Signatures, approvals, and audit trail)
*   [Tresorit](products/tresorit.md) (Secure file exchange for clients and counterparties)
*   [Paperless-ngx](products/paperless-ngx.md) (Mass indexing and OCR of legal discovery documents)
