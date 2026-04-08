# Odoo

**Category:** CRM, Accounting / Invoicing, HR
**Type:** Self-hosted or managed
**Jurisdiction:** Belgium (EU)
**Website:** [odoo.com](https://www.odoo.com)

## What It Is

Odoo is a modular business platform that covers CRM, invoicing, accounting, HR, project workflows, sales, and operations. For EuroDesk, it is a practical EU-based backbone when you want fewer separate tools and tighter business-process integration.

## EU Hosting Options

| Option | Description |
|---|---|
| **Odoo Online / Odoo.sh** | Managed service from an EU vendor |
| **Self-hosted** | Run on your own EU infrastructure |

## Good Fit For

- Sales pipelines and contact management
- Quotes, invoices, and bookkeeping workflows
- Employee records, leave requests, and HR processes
- Teams that prefer an integrated back office

## Self-Hosted Setup

### Requirements
- Ubuntu server
- PostgreSQL
- Domain name and SMTP server

### Install

```bash
sudo apt update
sudo apt install -y postgresql git python3-pip python3-venv build-essential libpq-dev
sudo adduser --system --home=/opt/odoo --group odoo
sudo -u postgres createuser -s odoo
git clone https://www.github.com/odoo/odoo --depth 1 --branch 17.0 /opt/odoo/src
python3 -m venv /opt/odoo/venv
/opt/odoo/venv/bin/pip install -r /opt/odoo/src/requirements.txt
```

### Basic Config

```ini
[options]
admin_passwd = change-me
db_host = False
db_port = False
db_user = odoo
db_password = False
xmlrpc_port = 8069
proxy_mode = True
```

### Start

```bash
/opt/odoo/venv/bin/python /opt/odoo/src/odoo-bin -c /etc/odoo.conf
```

## Recommended First Modules

1. CRM
2. Sales
3. Invoicing / Accounting
4. Employees
5. Time Off

## Key Features

- CRM and pipeline management
- Invoicing and accounting workflows
- HR records and leave management
- Large ecosystem of modules
- Self-hosted and managed options

## Trade-offs

- Broad scope means more setup than single-purpose tools
- Module sprawl can add complexity if not governed
- Accounting configuration should be reviewed by a local expert

## EuroDesk Verdict

Odoo fills several missing business-office categories at once and fits the EuroDesk model well thanks to its Belgian base and self-hosting path.
