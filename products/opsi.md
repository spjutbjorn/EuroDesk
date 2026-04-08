# opsi

**Category:** Endpoint Management / MDM
**Type:** Self-hosted
**Jurisdiction:** Germany (EU) via uib GmbH
**Website:** [opsi.org](https://www.opsi.org)

## What It Is

opsi is an open-source client management platform for deploying software, patching systems, inventorying endpoints, and automating workstation setup. It is aimed at organizations that want centralized endpoint control without handing device data to a US cloud vendor.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run opsi on your own EU-hosted infrastructure |

## Good Fit For

- Windows desktop fleet management
- Software rollouts across office devices
- Asset inventory and standardized workstation images
- On-prem endpoint control for schools, businesses, and public sector teams

## Core Capabilities

- Software deployment
- Patch and update rollout
- Hardware and software inventory
- OS installation automation
- Client grouping and policy targeting

## Basic Setup

### Requirements
- Debian or Ubuntu server
- DNS and DHCP control for provisioning use cases
- Managed client devices on the same network or connected by VPN

### Install

```bash
sudo apt update
sudo apt install -y opsi-server
sudo opsi-setup --auto-configure-samba
sudo opsi-setup --auto-configure-dhcpd
sudo opsi-setup --auto-configure-opsi-client-agent
```

### Access the Admin Interface

```bash
https://opsi.your-company.eu:4447
```

### Reverse Proxy Example

```nginx
server {
    listen 443 ssl;
    server_name opsi.your-company.eu;

    location / {
        proxy_pass https://localhost:4447;
        proxy_ssl_verify off;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

## Recommended First Use Cases

1. Deploy browser and office suite updates
2. Standardize VPN, password manager, and endpoint security clients
3. Inventory unmanaged devices
4. Automate onboarding for new employee laptops

## Key Features

- Central software deployment
- Patch management
- Inventory and reporting
- Automated client provisioning
- Strong fit for self-hosted EU infrastructure

## Trade-offs

- Stronger on desktop management than mobile-first MDM
- Works best with internal IT ownership
- Setup is more infrastructure-heavy than SaaS device management tools

## Compliance Notes

- **Jurisdiction:** Developed by uib GmbH, based in Mainz, Germany (EU).
- **Data Sovereignty:** Fully hostable on your own EU infrastructure. All client data and software logs stay on your servers.
- **Privacy:** As an open-source tool, there is no telemetry. You have full control over the management of all endpoints.
- **GDPR:** Fully compliant as a German company. You control all device and user metadata.

## EuroDesk Verdict

For organizations that need endpoint control as part of a sovereign office stack, opsi is a strong EU-native addition.
