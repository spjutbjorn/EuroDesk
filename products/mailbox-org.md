# Mailbox.org

**Category:** Email & Groupware
**Type:** Managed SaaS
**Jurisdiction:** Germany (EU, GDPR)
**Website:** [mailbox.org](https://mailbox.org)

## What It Is

Mailbox.org is a privacy-focused business email and groupware provider based in Berlin, Germany. It offers email, calendar, contacts, cloud storage, and video conferencing — powered entirely by open-source software and hosted in German data centers.

## Hosting Options

| Option | Description |
|---|---|
| **Mailbox.org managed** | Managed service hosted in German data centers |

## Plans

| Plan | Price | Storage | Notes |
|---|---|---|---|
| **Light** | 1 €/mo | 2 GB mail + 2 GB cloud | Basic email |
| **Standard** | 3 €/mo | 10 GB mail + 5 GB cloud | Full groupware |
| **Premium** | 9 €/mo | 25 GB mail + 25 GB cloud | Priority support |
| **Business (teams)** | Volume pricing | Custom | Custom domain, admin panel |

## Setup for a Team

### 1. Create a Business Account

1. Sign up at [mailbox.org/business](https://mailbox.org/business)
2. Choose a plan and number of mailboxes
3. Verify your organization

### 2. Configure Custom Domain

In the admin panel under **Domains**:

1. Add your domain
2. Set MX records:
   ```
   MX  10  mxext1.mailbox.org
   MX  10  mxext2.mailbox.org
   MX  10  mxext3.mailbox.org
   ```
3. Add SPF record:
   ```
   TXT  "v=spf1 include:mailbox.org ~all"
   ```
4. Add DKIM (keys provided in admin panel):
   ```
   TXT  mbo0001._domainkey  "v=DKIM1; k=rsa; p=..."
   ```
5. Add DMARC:
   ```
   TXT  _dmarc  "v=DMARC1; p=reject; rua=mailto:dmarc@your-company.eu"
   ```

### 3. Create Mailboxes

In the admin panel:
- **Mailboxes** → **New Mailbox**
- Set username, display name, password
- Assign to your custom domain

### 4. Desktop Client Configuration (IMAP/SMTP)

| Setting | Value |
|---|---|
| IMAP server | imap.mailbox.org |
| IMAP port | 993 (SSL/TLS) |
| SMTP server | smtp.mailbox.org |
| SMTP port | 465 (SSL/TLS) |
| Authentication | Username (full email) + password |

Compatible with Thunderbird, Apple Mail, Outlook.

## Included Services

| Service | Description |
|---|---|
| **Email** | Full-featured IMAP/SMTP with webmail |
| **Calendar** | CalDAV-based, shareable team calendars |
| **Contacts** | CardDAV-based address book |
| **Cloud Storage** | Based on Nextcloud |
| **Video Calls** | Based on Jitsi Meet |
| **Office** | OnlyOffice for document editing |
| **OpenPGP** | Built-in PGP key management in webmail |

## Key Features

- Full OpenPGP encryption support in webmail
- Guard (mailbox.org Guard) for encrypted external emails
- Alias addresses and catch-all
- Spam and virus filtering (Rspamd + ClamAV)
- Two-factor authentication (TOTP)
- Powered by 100% renewable energy

## Compliance Notes

- All servers in Germany
- Subject to EU GDPR and BDSG
- Data Processing Agreement (DPA) available
- No advertising, no data selling
- Audited annually for ISO 27001 (verify current status on their site)

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Google Workspace | US jurisdiction, data processed in USA |
| Microsoft 365 | US company, EU boundary requires extra configuration |
| Proton Mail | Excellent privacy but Swiss jurisdiction, not EU |
