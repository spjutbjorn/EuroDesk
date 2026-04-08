# GLPI

**Category:** Asset Management / CMDB
**Type:** Self-hosted or managed
**Jurisdiction:** France (EU) via Teclib
**Website:** [glpi-project.org](https://glpi-project.org)

## What It Is

GLPI is an open-source IT asset management and CMDB platform for tracking hardware, software, contracts, suppliers, and relationships between systems. It fills the operational inventory gap in EuroDesk and works well alongside endpoint management and helpdesk tooling.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run GLPI on your own EU servers |
| **Managed by EU provider** | Use hosting from an EU or adequacy-country operator |

## Good Fit For

- Laptop and server inventory
- Software license tracking
- CMDB relationships between services and assets
- Contract and supplier tracking

## Self-Hosted Setup

### Requirements
- Linux server
- MariaDB or MySQL
- PHP 8.1+
- nginx or Apache

### Install

```bash
wget https://github.com/glpi-project/glpi/releases/latest/download/glpi.tgz
tar -xzf glpi.tgz
sudo mv glpi /var/www/glpi
sudo chown -R www-data:www-data /var/www/glpi
```

### Database

```bash
mysql -u root -p
CREATE DATABASE glpi;
CREATE USER 'glpi'@'localhost' IDENTIFIED BY 'change-me';
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';
FLUSH PRIVILEGES;
```

## Compliance Notes

- Restrict CMDB access because asset records often include employee, vendor, and network details.
- Keep contract, supplier, and inventory exports within EU-controlled storage.
- Integrate with SSO and audit admin activity.

## Key Features

- Asset inventory and lifecycle tracking
- Software and license management
- Contracts, suppliers, and financial tracking
- CMDB-style relationships
- Strong EU fit for self-hosted operations

## Trade-offs

- Broad ITSM scope can feel heavy for tiny teams
- Best results come from disciplined asset ownership
- Advanced workflows may need plugins or integration work

## EuroDesk Verdict

GLPI closes the asset and CMDB gap while also supporting procurement and contract metadata that many office stacks eventually need.
