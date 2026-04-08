# EuroDesk Migration Guide

A practical playbook for moving an organization from US-dependent tools to the EuroDesk sovereign stack.

## Phase 0: Assessment (Week 1-2)

### Inventory current tools
1. List every SaaS product, cloud service, and internal tool in use
2. Map each tool to the EuroDesk equivalent using [core.md](core.md)
3. For each tool, document: number of users, data sensitivity, contract renewal date, and integration dependencies

### Prioritize using the Migration Priority Matrix
1. Open [migration_priority.html](migration_priority.html) and adjust dimension weights for your organization
2. Score each product — focus on the top-ranked items first
3. Use [conversion_calculator.html](conversion_calculator.html) to estimate total cost and effort

### Identify quick wins
- Tools with no data migration needed (search engines, browsers, VPNs) can switch immediately
- Tools approaching contract renewal are natural migration points

## Phase 1: Foundation (Week 3-6)

Migrate the **Universal Base Stack** first — everything else depends on these.

### 1. Identity & Access (ZITADEL)
- Deploy ZITADEL as the central identity provider
- Configure SSO/SAML for all subsequent tools
- **Why first:** Every other tool needs authentication

### 2. Email (Proton Mail / Tuta / Mailbox.org)
- Export mailboxes from Google Workspace / M365
- Set up domains, MX records, SPF/DKIM/DMARC
- Migrate contacts and calendars
- **Parallel:** Keep old email running in receive-only mode during transition (2-4 weeks)

### 3. File Storage (Nextcloud)
- Deploy Nextcloud on EU hosting (Hetzner, IONOS, OVH)
- Migrate files from Google Drive / OneDrive using Nextcloud migration tools
- Install Collabora Online or ONLYOFFICE for document editing
- **Data migration tip:** Use `rclone` for bulk transfers

### 4. Communication (Mattermost or Element)
- Deploy and configure channels mirroring current Slack/Teams structure
- Set up integrations (webhooks, bots)
- **Cutover strategy:** Run parallel for 1 week, then disable old platform

### 5. Password Manager (Bitwarden self-hosted or Passbolt)
- Export from LastPass/1Password
- Import into new vault
- Enforce MFA across organization

### 6. VPN & Browser
- Roll out Mullvad VPN to all endpoints
- Deploy Mullvad Browser or configure Firefox with privacy settings
- Switch default search to Startpage or Qwant

## Phase 2: Department-Specific Tools (Week 7-14)

Migrate per department, ordered by priority matrix score.

### High-priority migrations

| Department | From | To | Key steps |
|---|---|---|---|
| **Finance** | SAP/Dynamics | Odoo | Chart of accounts mapping, historical data import, VAT configuration |
| **HR** | Workday/BambooHR | Personio | Employee records export, payroll integration, leave balances |
| **Helpdesk** | Zendesk | Zammad | Ticket history import, SLA configuration, email piping |
| **Analytics** | Google Analytics | Matomo/Plausible | Install tracking code, verify data parity, remove GA |
| **DevOps** | GitHub | Forgejo | Repository migration (`git push --mirror`), CI/CD pipeline rewrite |
| **AI tools** | ChatGPT/Copilot | Mistral/Langdock | API key swap, prompt testing, evaluate output quality |

### Migration patterns

**SaaS to SaaS:** Export data from old provider, import into EU alternative. Verify data integrity.

**SaaS to Self-hosted:** Provision EU infrastructure first, deploy application, migrate data, test, then cutover.

**API swap:** For developer tools, change API endpoints and keys. Run parallel validation before decommissioning.

## Phase 3: Infrastructure (Week 10-18)

### Cloud migration (if applicable)
1. Audit current AWS/Azure/GCP usage (compute, storage, databases, managed services)
2. Map each service to EU equivalent:
   - **Compute:** Hetzner Cloud, OVH, Scaleway
   - **Kubernetes:** Self-managed on EU providers or STACKIT
   - **Object storage:** OVH Object Storage, Scaleway S3-compatible
   - **Managed databases:** Check EU provider offerings or run self-managed
3. Migrate workloads in order: staging first, then production
4. Update DNS, load balancers, and monitoring
5. Decommission US cloud resources only after 30-day parallel run

### AI infrastructure (if using LLMs)
1. Deploy EULLM or Ollama on EU GPU hosting (Genesis Cloud, Verda, OVH)
2. Set up Open WebUI or Langdock as the user-facing interface
3. Test model quality against previous ChatGPT/Claude outputs
4. Configure prompt caching and model routing for cost optimization

## Phase 4: Verification & Compliance (Week 16-20)

### Data residency audit
- [ ] All email data stored in EU
- [ ] All file storage on EU infrastructure
- [ ] All databases on EU-owned hosting
- [ ] All backups on EU infrastructure
- [ ] No US-owned cloud services in production
- [ ] DNS hosted by EU provider
- [ ] No telemetry/analytics sending data outside EU

### GDPR documentation
- [ ] Data processing agreements (DPAs) signed with all EU providers
- [ ] Records of processing activities (ROPA) updated
- [ ] Data Protection Impact Assessment (DPIA) for high-risk processing
- [ ] Subprocessor list documented for each tool
- [ ] Employee privacy notices updated

### Security baseline
- [ ] SSO enforced across all tools via ZITADEL
- [ ] MFA enabled for all users
- [ ] Wazuh deployed for endpoint monitoring
- [ ] Grafana + Loki collecting logs from all services
- [ ] Bareos backup schedules verified and tested
- [ ] Incident response plan updated for new stack

## Common Pitfalls

| Pitfall | Mitigation |
|---|---|
| **Big bang migration** | Migrate in phases; never cut over everything at once |
| **Ignoring integrations** | Map all tool-to-tool integrations before starting; some may need n8n workflows to bridge |
| **Underestimating email migration** | Email is the hardest — plan 4 weeks overlap, test SPF/DKIM thoroughly |
| **Forgetting mobile devices** | MDM policies need updating; test EU tools on mobile before rollout |
| **Contract lock-in** | Check renewal dates early; some contracts have 60-90 day cancellation windows |
| **User resistance** | Involve power users early; run training sessions per department |
| **Self-hosted maintenance** | Budget for ongoing ops; consider managed EU options if team is small |

## Timeline Summary

| Phase | Duration | Focus |
|---|---|---|
| **Phase 0** | Week 1-2 | Assessment, prioritization, cost estimation |
| **Phase 1** | Week 3-6 | Foundation: identity, email, files, chat, passwords, VPN |
| **Phase 2** | Week 7-14 | Department-specific tools |
| **Phase 3** | Week 10-18 | Cloud infrastructure migration |
| **Phase 4** | Week 16-20 | Verification, compliance, documentation |

Phases 2 and 3 overlap intentionally — department tools and infrastructure can migrate in parallel.

**Total estimated timeline: 4-5 months** for a mid-sized organization (50-500 employees).
