# LimeSurvey

**Category:** Forms / Surveys
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU) via LimeSurvey GmbH
**Website:** [limesurvey.org](https://www.limesurvey.org)

## What It Is

LimeSurvey is an open-source survey and form platform for questionnaires, feedback collection, internal polls, consent forms, and research projects. It is especially useful when you need data collection inside European hosting and compliance boundaries.

## EU Hosting Options

| Option | Description |
|---|---|
| **LimeSurvey Cloud** | Managed service from an EU vendor |
| **Self-hosted** | Deploy on your own EU server |

## Good Fit For

- Customer or employee surveys
- Internal request forms
- Research data collection
- Event registration forms

## Self-Hosted Setup

### Requirements
- Linux server
- PHP 8.1+
- MariaDB or PostgreSQL
- nginx or Apache

### Install

```bash
wget https://download.limesurvey.org/latest-stable-release/limesurvey6.x-latest.zip
unzip limesurvey6.x-latest.zip
mv limesurvey /var/www/limesurvey
chown -R www-data:www-data /var/www/limesurvey
```

### Database

```bash
sudo -u postgres createuser limesurvey
sudo -u postgres createdb limesurvey
```

### nginx Example

```nginx
server {
    listen 443 ssl;
    server_name forms.your-company.eu;
    root /var/www/limesurvey;
    index index.php;

    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    location ~ \\.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php8.2-fpm.sock;
    }
}
```

## Recommended Controls

- Minimize personal data collection
- Use explicit retention periods
- Restrict admin accounts with SSO if possible
- Export results to your document system and back them up

## Key Features

- Branching logic and conditional questions
- Anonymous or named responses
- Multi-language surveys
- Self-hosted or managed deployment
- Strong fit for compliance-sensitive data collection

## Trade-offs

- More form-focused than full document workflow platforms
- Needs maintenance if self-hosted
- UI is functional rather than lightweight and minimal

## EuroDesk Verdict

LimeSurvey is a strong addition for teams that need structured data collection without sending responses to a US SaaS form platform.
