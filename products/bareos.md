# Bareos

**Category:** Backup / Disaster Recovery
**Type:** Self-hosted
**Jurisdiction:** Germany (EU) via Bareos GmbH & Co. KG
**Website:** [bareos.com](https://www.bareos.com)

## What It Is

Bareos is an open-source enterprise backup platform for servers, databases, VMs, and workstations. It is designed for scheduled backups, retention policies, cataloging, and full restore workflows — making it a strong fit for business continuity inside an EU-controlled environment.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run Bareos on your own EU-owned infrastructure |

## Good Fit For

- Central backups for Linux and Windows servers
- Long retention policies and tape or disk targets
- Restore testing and disaster recovery planning
- Compliance-heavy environments that need auditability

## Plans (2026)

| Plan | Price | Minimum |
|---|---|---|
| **Subscription** | €48 /unit/year | 10 units (€480/yr) |
| **Basic Support**| ~€2,850 /year | 8/5 support, up to 20 units |
| **Standard/Premium**| Custom | Higher unit counts & 24/7 SLAs |

> **Units:** Calculated based on either total source data (per TB) or total number of clients + plugin jobs.

## Core Components

| Component | Purpose |
|---|---|
| **Director** | Schedules jobs and coordinates restores |
| **Storage Daemon** | Writes backup data to disk, tape, or object-backed storage |
| **File Daemon** | Runs on protected systems and sends data |
| **Catalog** | PostgreSQL database with backup metadata |
| **WebUI** | Browser interface for monitoring and restore operations |

## Basic Setup

### Requirements
- Ubuntu or Debian server
- PostgreSQL
- Backup storage volume with enough capacity

### Install

```bash
curl -fsSL https://download.bareos.org/current/xUbuntu_22.04/add_bareos_repositories.sh | sudo bash
sudo apt update
sudo apt install -y bareos bareos-database-postgresql postgresql
```

### Create Catalog

```bash
sudo -u postgres createuser bareos
sudo -u postgres createdb bareos
sudo /usr/lib/bareos/scripts/create_bareos_database
sudo /usr/lib/bareos/scripts/make_bareos_tables
sudo /usr/lib/bareos/scripts/grant_bareos_privileges
```

### Start Services

```bash
sudo systemctl enable --now bareos-dir bareos-sd bareos-fd
```

## What to Back Up First

1. Password manager data
2. Mail and document storage
3. Databases for project tools and wikis
4. Identity and SSO configuration
5. Off-site encrypted backup copies

## Recommended Policy

- Daily incremental backups
- Weekly full backups
- Monthly restore test
- One offline or off-site copy
- Separate backup credentials from production credentials

## Key Features

- Central scheduling and retention policies
- File-level and system-level restores
- PostgreSQL-backed catalog
- Multi-client backups
- Enterprise support available from an EU vendor

## Trade-offs

- More operationally heavy than simple sync-based backup tools
- Initial configuration is more complex than lightweight backup products
- Best value appears when protecting multiple systems

## Compliance Notes

- **Jurisdiction:** Developed by Bareos GmbH & Co. KG, based in Cologne, Germany (EU).
- **GDPR:** Complies with EU GDPR and German data protection laws (BDSG).
- **Data Sovereignty:** All backup data, catalogs, and logs stay on your infrastructure.
- **Privacy:** As an open-source tool, there is no telemetry. You have full control over the encryption of backup data before it is stored.
- Ensure that backup volumes and catalogs are securely handled, as they may contain personal data from multiple systems.

## EuroDesk Verdict

Bareos fills a major gap in EuroDesk: a serious EU backup and disaster recovery layer for the rest of the stack.
