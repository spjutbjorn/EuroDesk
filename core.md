# EuroDesk Core Product Mapping

This document maps the EuroDesk sovereign office stack to the most common white-collar roles. To maintain efficiency and privacy, each role starts with a "Universal Base Stack" and adds only the essential specialized tools required for their daily operations.

## 0. Universal Base Stack (Mandatory for All)
*The essential foundation for any sovereign office workstation.*
*   **Email & Productivity:** [Proton Mail](products/proton-mail.md), [Tuta](products/tuta.md), or [Mailbox.org](products/mailbox-org.md).
*   **Chat & Collaboration:** [Element](products/element-matrix.md), [Mattermost](products/mattermost.md), and [Jitsi Meet](products/jitsi-meet.md).
*   **File Storage & Editing:** [Nextcloud](products/nextcloud.md) with [ONLYOFFICE](products/onlyoffice.md) or [Collabora Online](products/collabora.md).
*   **Security & Browsing:** [Passbolt](products/passbolt.md), [Mullvad VPN](products/mullvad.md), and [Mullvad Browser](products/mullvad-browser.md).
*   **Search:** [Startpage](products/startpage.md) or [Qwant](products/qwant.md).

---

## 1. Role-Specific Core Add-ons

### 💼 Administration & Office Support
*   [Easy!Appointments](products/easyappointments.md) (Scheduling & Meeting Slots)
*   [Documenso](products/documenso.md) (Electronic Signatures for approvals)
*   [CryptPad](products/cryptpad.md) (Secure, end-to-end encrypted temporary documents)

### 📈 Management & Leadership
*   [OpenProject](products/openproject.md) (Timelines, Gantt charts, and resource planning)
*   [Planka](products/planka.md) (Team-level Kanban boards)
*   [n8n](products/n8n.md) (Workflow automation between departments)

### ⚖️ Business, Finance & Legal
*   [Odoo](products/odoo.md) (Full accounting, VAT, and invoicing engine)
*   [Documenso](products/documenso.md) (Contract signing and tracking)
*   [SwissTransfer](products/swisstransfer.md) (Secure, large file transfers for sensitive documents)

### 📣 Sales, Marketing & Communication
*   [Odoo](products/odoo.md) (CRM & Lead Management)
*   [Brevo](products/brevo.md) or [MailerLite](products/mailerlite.md) (Compliant Newsletters & Campaigns)
*   [Matomo](products/matomo.md) (Marketing and web analytics)
*   [Tally](products/tally.md) (Simple form building for lead acquisition)

### 👥 Human Resources (HR)
*   [Personio](products/personio.md) (Employee lifecycle and records management)
*   [Recruitee](products/recruitee.md) (Applicant tracking and hiring pipelines)
*   [Odoo](products/odoo.md) (Payroll and expense management)

### 💻 Information Technology (IT) & Data
*   [Forgejo](products/forgejo.md) (Git hosting, CI/CD, and package registry)
*   [ZITADEL](products/zitadel.md) (Identity Management & Single Sign-On across the stack)
*   [Grafana + Loki](products/grafana-loki.md) (System-wide observability and logging)
*   [Wazuh](products/wazuh.md) (Security monitoring and vulnerability detection)
*   [opsi](products/opsi.md) (Automated software deployment for endpoints)

### 🛠️ Customer Success & Support
*   [Zammad](products/zammad.md) (Helpdesk, ticket management, and service desk)
*   [n8n](products/n8n.md) (Automating support-to-engineering escalations)

### 🎨 Creative & Design Services
*   [Penpot](products/penpot.md) (Design, prototyping, and SVG-based UI/UX)
*   [Outline](products/outline.md) (Design system documentation and knowledge base)

### 🏗️ Specialized (Consulting & Engineering)
*   [GLPI](products/glpi.md) (IT asset and hardware management)
*   [Bareos](products/bareos.md) (Disaster recovery and backup for technical projects)
*   [DeepL](products/deepl.md) (High-accuracy translation for technical consulting)

### 🔬 Research, Development & Innovation (RDI)
*   [Logseq](products/logseq.md) or [AppFlowy](products/appflowy.md) (Personal/Team knowledge graphing)
*   [Forgejo](products/forgejo.md) (IP/Code repository)

### 🏛️ Public Administration & Government
*   [LimeSurvey](products/limesurvey.md) (Formal citizen feedback and research surveys)
*   [Documenso](products/documenso.md) (Official decision and permit signing)

### 📦 Procurement & Supply Chain
*   [Odoo](products/odoo.md) (Inventory, warehouse, and purchasing management)
*   [GLPI](products/glpi.md) (Supplier and maintenance contract tracking)

### 🎓 Education & Training
*   [Tally](products/tally.md) (Online tests, registration, and student feedback)
*   [Jitsi Meet](products/jitsi-meet.md) (Classroom-style video delivery)

### 🌍 Non-Profit & NGO Operations
*   [LimeSurvey](products/limesurvey.md) (Project outcome and donor reporting)
*   [CryptPad](products/cryptpad.md) (High-sensitivity advocacy and policy documentation)

### 🏥 Healthcare Admin
*   [ZITADEL](products/zitadel.md) (Strict patient data access control and identity)
*   [Documenso](products/documenso.md) (Medical consent and administrative signing)

### 🚀 Product, Strategy & Business Operations
*   [Apache Superset](products/apache-superset.md) (BI Dashboards and strategic metrics)
*   [n8n](products/n8n.md) (Operational process automation)
*   [OpenProject](products/openproject.md) (Roadmap and strategic execution)

### 🏦 Banking, Insurance & Finance
*   [Wazuh](products/wazuh.md) (Regulatory compliance monitoring and audit logging)
*   [ZITADEL](products/zitadel.md) (Customer-facing identity and high-assurance auth)

### 🏠 Real Estate & Facilities
*   [GLPI](products/glpi.md) (Building maintenance and facility asset tracking)
*   [Odoo](products/odoo.md) (Lease billing and financial contracts)

### 📰 Media, Publishing & Editorial
*   [Collabora Online](products/collabora.md) (Fine-grained document track-changes and review)
*   [Outline](products/outline.md) (Knowledge base and internal editorial guides)

### 🚛 Logistics, Transportation & Fleet Management
*   [Odoo](products/odoo.md) (Inventory, shipping, and routing management)
*   [GLPI](products/glpi.md) (Fleet, vehicle, and asset tracking)
*   [n8n](products/n8n.md) (Automating tracking and dispatch notifications)

### 🏨 Hospitality, Tourism & Travel Management
*   [Odoo](products/odoo.md) (POS, bookings, and customer billing)
*   [Easy!Appointments](products/easyappointments.md) (Service and slot-based bookings)
*   [n8n](products/n8n.md) (Connecting booking engines to internal systems)

### ⚡ Energy, Utilities & Environmental Services
*   [Apache Superset](products/apache-superset.md) (Grid and energy market visualizations)
*   [Wazuh](products/wazuh.md) (Operational monitoring of critical management systems)
*   [Odoo](products/odoo.md) (Project and maintenance management)

### 🛍️ Retail & E-commerce Operations
*   [PrestaShop](products/prestashop.md) or [Shopware](products/shopware.md) (European-native e-commerce engines)
*   [Odoo](products/odoo.md) (Omnichannel retail inventory and POS)
*   [Matomo](products/matomo.md) (Privacy-compliant conversion and sales analytics)

### 🖼️ Arts, Culture & Museum Management
*   [GLPI](products/glpi.md) (Collection management and artifact tracking)
*   [Nextcloud](products/nextcloud.md) (High-resolution asset storage and sharing)
*   [CryptPad](products/cryptpad.md) (Collaborative planning for sensitive exhibitions)

### 🌍 Translation, Interpretation & Localization
*   [DeepL](products/deepl.md) (Professional-grade AI translation and API)
*   [Nextcloud](products/nextcloud.md) (Secure file exchange for large translation projects)
*   [Outline](products/outline.md) (Terminology management and shared glossaries)

### 📐 Architecture, Urban Planning & Construction Management
*   [Nextcloud](products/nextcloud.md) (Large-scale document and CAD/BIM model management)
*   [OpenProject](products/openproject.md) (Complex construction timelines and project tasks)
*   [Documenso](products/documenso.md) (Signing of technical approvals and site plans)

### 🛡️ Safety, Quality & Regulatory Compliance (QHSE)
*   [Wazuh](products/wazuh.md) (Audit trails, file integrity, and security monitoring)
*   [ZITADEL](products/zitadel.md) (Identity governance and high-assurance access controls)
*   [Odoo](products/odoo.md) (Quality control, audit logs, and non-conformance tracking)
