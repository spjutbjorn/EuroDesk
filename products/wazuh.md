# Wazuh

**Category:** Security Monitoring / Endpoint Security
**Type:** Self-hosted or managed
**Jurisdiction:** Spain (EU)
**Website:** [wazuh.com](https://wazuh.com)

## What It Is

Wazuh is an open-source security platform for endpoint monitoring, vulnerability detection, file integrity monitoring, log analysis, and incident investigation. It gives EuroDesk a security operations layer that complements backups, identity, and endpoint management.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Wazuh on your own EU-controlled infrastructure |
| **Managed by EU provider** | Use a managed deployment operated by an EU vendor |

## Good Fit For

- Endpoint visibility across servers and workstations
- Security event monitoring
- Vulnerability and configuration monitoring
- Compliance-oriented audit trails

## Self-Hosted Setup

### Quick Install

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
curl -sO https://packages.wazuh.com/4.8/config.yml
sudo bash ./wazuh-install.sh --generate-config-files
sudo bash ./wazuh-install.sh --wazuh-indexer node-1
sudo bash ./wazuh-install.sh --wazuh-server wazuh-1
sudo bash ./wazuh-install.sh --wazuh-dashboard dashboard
```

### Agent Install Example

```bash
curl -so wazuh-agent.deb https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.x.x-1_amd64.deb
sudo WAZUH_MANAGER='wazuh.your-company.eu' dpkg -i ./wazuh-agent.deb
sudo systemctl enable --now wazuh-agent
```

## Compliance Notes

- Security logs often contain personal and operational data, so define retention and access controls early.
- Keep indexer and dashboard storage on EU-owned infrastructure.
- Review agent policies to avoid collecting unnecessary user data.

## Key Features

- Endpoint monitoring and alerting
- Vulnerability detection
- File integrity monitoring
- Security dashboards and search
- Strong fit for self-hosted European deployments

## Trade-offs

- Requires tuning to avoid noisy alerts
- Best used with clear ownership and incident workflows
- Larger environments should plan storage and retention carefully

## EuroDesk Verdict

Wazuh adds the security monitoring layer that a complete office platform usually needs once core collaboration tools are in place.
