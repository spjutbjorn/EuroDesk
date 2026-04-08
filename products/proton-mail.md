# Proton Mail

**Category:** Email
**Type:** Managed SaaS
**Jurisdiction:** Switzerland (equivalent EU protection, subject to Swiss FADP)
**Website:** [proton.me](https://proton.me)

## What It Is

Proton Mail is an end-to-end encrypted email service headquartered in Geneva, Switzerland. Switzerland has data protection laws equivalent to EU GDPR. Proton Mail is widely used as a privacy-first alternative to Gmail and Outlook.

## Hosting Options

| Option | Description |
|---|---|
| **Proton managed** | Managed service operated from Switzerland |

## Plans (Business)

| Plan | Price (Annually) | Storage | Key Features |
|---|---|---|---|
| **Mail Essentials** | $6.99 /user/mo | 15 GB | 3 domains, basic Proton Meet |
| **Workspace Standard** | $12.99 /user/mo | 1 TB | 15 domains, VPN & Pass included |
| **Workspace Premium** | $19.99 /user/mo | 3 TB | Lumo AI, Proton Scribe, Advanced Compliance |

## Setup for a Team

### 1. Create a Proton for Business Account

1. Go to [proton.me/business](https://proton.me/business)
2. Choose a plan and create an admin account
3. Verify your domain

### 2. Domain Verification and MX Records

Add these DNS records at your domain registrar:

```
# MX records
MX  10  mail.protonmail.ch
MX  20  mailsec.protonmail.ch

# SPF
TXT  "v=spf1 include:_spf.protonmail.ch ~all"

# DKIM (values provided in Proton admin panel)
CNAME  protonmail._domainkey  protonmail.domainkey.<unique>.domains.proton.ch

# DMARC
TXT  _dmarc  "v=DMARC1; p=quarantine; rua=mailto:dmarc@your-company.eu"
```

### 3. Create User Accounts

In the Proton admin panel:
- **Users & Addresses** → Add user
- Set email address, temporary password
- User completes account setup on first login

### 4. Proton Bridge (IMAP/SMTP for desktop clients)

For users who prefer a native email client (Thunderbird, Apple Mail):

1. Download [Proton Bridge](https://proton.me/mail/bridge) on the user's computer
2. Sign in with Proton credentials
3. Bridge exposes local IMAP (127.0.0.1:1143) and SMTP (127.0.0.1:1025)
4. Configure your mail client to use those local ports

## Key Features

- End-to-end encryption between Proton users (automatic)
- Zero-access encryption for all stored mail
- Custom domain support
- Aliases and catch-all addresses
- Proton Calendar included
- Proton Drive included (file storage)
- iOS and Android apps
- Web client

## Compliance Notes

- Servers in Switzerland (FADP, equivalent to GDPR)
- No access to email content even for Proton staff
- Proton has published transparency reports
- Data Processing Agreement (DPA) available for business accounts
- Swiss authorities have jurisdiction, not US CLOUD Act

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Gmail / Google Workspace | US company, data accessible under US law |
| Microsoft 365 / Outlook | US company, complex EU data boundary setup |
| iCloud Mail | US company |
