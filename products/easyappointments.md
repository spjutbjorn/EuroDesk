# Easy!Appointments

**Category:** Scheduling / Booking
**Type:** Self-hosted
**Jurisdiction:** EU-hostable when self-hosted
**Website:** [easyappointments.org](https://easyappointments.org)

## What It Is

Easy!Appointments is an open-source booking system for appointment scheduling, meeting slots, and service calendars. It is useful when a team needs customer or internal booking workflows without relying on a US SaaS scheduling platform.

## Good Fit For

- Consultation booking
- Internal support appointments
- Interview scheduling
- Team or department booking pages

## Self-Hosted Setup

### Requirements
- Linux server
- PHP
- MySQL or MariaDB
- nginx or Apache

### Install

```bash
git clone https://github.com/alextselegidis/easyappointments.git
sudo mv easyappointments /var/www/easyappointments
sudo chown -R www-data:www-data /var/www/easyappointments
```

### Database

```bash
mysql -u root -p
CREATE DATABASE easyappointments;
CREATE USER 'ea'@'localhost' IDENTIFIED BY 'change-me';
GRANT ALL PRIVILEGES ON easyappointments.* TO 'ea'@'localhost';
FLUSH PRIVILEGES;
```

### nginx Example

```nginx
server {
    listen 443 ssl;
    server_name book.your-company.eu;
    root /var/www/easyappointments;
    index index.php;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \\.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php8.2-fpm.sock;
    }
}
```

## Recommended Uses

1. Public booking for consultations
2. Internal IT support slots
3. Interview scheduling pages
4. Shared department appointment calendars

## Key Features

- Booking pages and availability management
- Calendar sync support
- Custom services and providers
- Fully self-hosted deployment

## Trade-offs

- More specialized and lighter than a full groupware platform
- You own maintenance and email delivery
- Advanced enterprise workflow needs may require customization

## EuroDesk Verdict

Easy!Appointments fills the scheduling gap with a simple self-hosted approach that keeps booking data on infrastructure you control.
