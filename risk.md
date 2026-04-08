# EuroDesk Risk Management

This document outlines the operational, legal, and technical risks associated with running a sovereign European office stack and the recommended mitigation strategies.

## 1. Operational Complexity (The Self-Hosting Burden)
*   **Risk:** Many tools in this stack require self-hosting. Managing security patches, backups, and uptime for 30+ separate applications creates significant IT overhead.
*   **Impact:** System downtime or unpatched vulnerabilities leading to data breaches.
*   **Mitigation:** Standardize on Docker/Kubernetes; use centralized logging (Loki) and monitoring (Grafana/Wazuh); consider professional managed services from EU-owned vendors for mission-critical apps.

## 2. Upstream Supply Chain & Silent Telemetry
*   **Risk:** Even if a tool is open-source and self-hosted, the *code* may contain default settings that reach out to US-based services (e.g., Gravatar, Google Fonts, update checkers, or hardcoded telemetry).
*   **Impact:** Metadata or IP addresses leaked to US jurisdictions, potentially violating strict "sovereign" requirements.
*   **Mitigation:** Implement strict egress firewall rules; audit configuration files for telemetry settings; use privacy-focused defaults (e.g., local fonts, Libravatar).

## 3. Provider Acquisition (Ownership Drift)
*   **Risk:** An EU-based provider (e.g., a hosting company or SaaS vendor) could be acquired by a US-based entity.
*   **Impact:** The provider would immediately become subject to the US CLOUD Act, invalidating its sovereign status.
*   **Mitigation:** Maintain an exit strategy; prioritize open standards (IMAP, WebDAV, Matrix) to ensure data can be migrated to a new EU provider quickly.

## 4. Regulatory & Adequacy Drift
*   **Risk:** "Adequacy Decisions" (e.g., for Switzerland or the UK) can be revoked or challenged in the EU Court of Justice.
*   **Impact:** Legal uncertainty regarding data transfers to previously "safe" jurisdictions.
*   **Mitigation:** Monitor CJEU rulings; focus primary operations in EU/EEA member states for the highest long-term legal stability.

## 5. Shadow IT & User Resistance
*   **Risk:** Employees may find open-source or sovereign alternatives less "polished" than US hyperscaler tools (e.g., M365, Slack, ChatGPT).
*   **Impact:** Users bypassing the stack to use unauthorized US-based tools, creating massive compliance gaps.
*   **Mitigation:** Invest in UX/onboarding; ensure SSO (ZITADEL) is seamless; highlight the privacy "feature" as a company value.

## 6. Scaling & Performance
*   **Risk:** Some open-source tools may not scale as efficiently as US hyperscale clouds for very large organizations (10,000+ users).
*   **Impact:** Performance degradation or prohibitive infrastructure costs.
*   **Mitigation:** Perform load testing; use professional enterprise versions of OSS tools (e.g., Nextcloud Enterprise, Mattermost Enterprise) which are tuned for scale.

## 7. AI Act Compliance
*   **Risk:** The new EU AI Act introduces strict transparency and risk management rules for AI models.
*   **Impact:** Financial penalties or forced shutdown of non-compliant AI implementations.
*   **Mitigation:** Prioritize models with "Transparency Cards" (Mistral, Aleph Alpha); use EULLM for model auditing; maintain a registry of all AI use cases.
