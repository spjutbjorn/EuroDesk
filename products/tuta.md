# Tuta (formerly Tutanota)

**Category:** Email
**Type:** Managed SaaS
**Jurisdiction:** Germany (EU, GDPR)
**Website:** [tuta.com](https://tuta.com)

## What It Is

Tuta is an encrypted email and calendar service based in Hannover, Germany. All data is stored in Germany, making it fully subject to EU GDPR and German data protection law (BDSG), which is among the strictest in the world.

## Hosting Options

| Option | Description |
|---|---|
| **Tuta managed** | Managed service hosted in Germany |

## Plans (Business)

| Plan | Price (Yearly) | Storage | Domains |
|---|---|---|---|
| **Essential** | €6 /user/mo | 50 GB | 3 |
| **Advanced** | €8 /user/mo | 500 GB | 10 |
| **Unlimited** | €12 /user/mo | 1 TB | Unlimited |

## Setup for a Team

### 1. Create a Team Account

1. Go to [tuta.com/pricing](https://tuta.com/pricing)
2. Select a business plan
3. Create the admin account with your company email

### 2. Add Custom Domain

In the admin portal under **Domains**:

1. Enter your domain (e.g., `your-company.eu`)
2. Add verification TXT record:
   ```
   TXT  tutanota-verification=...
   ```
3. Update MX records:
   ```
   MX  10  mail.tutanota.de
   ```
4. Add SPF:
   ```
   TXT  "v=spf1 include:spf.tutanota.de ~all"
   ```
5. Add DKIM (provided in admin panel)

### 3. Create Users

In **Manage Users**:
- Click **Add User**
- Set name and email address
- User receives invite to set their password

### 4. Configure Groups (Shared Mailboxes)

Tuta supports shared mailboxes as **Groups**:
- Go to **Groups** → **Add Group**
- Add members
- Each member can access and send from the shared mailbox

## Key Features

- End-to-end encryption (all emails, calendar, contacts)
- Encrypted subject lines (unique among email providers)
- Encrypted calendar (Tuta Calendar)
- Custom domain support
- Catch-all and aliases
- Offline mode in desktop and mobile apps
- No ads, no tracking
- Open source (client-side code)

## Sending Encrypted Emails to External Recipients

When emailing a non-Tuta user, Tuta can send an encrypted message with a shared password:

1. Compose email as normal
2. Click the lock icon to enable external encryption
3. Set a password (share with recipient via a separate channel)
4. Recipient opens a secure link in their browser to read the message

## Compliance Notes

- Servers exclusively in Germany
- Subject to German BDSG and EU GDPR
- No US CLOUD Act applicability
- Zero-access encryption: Tuta staff cannot read your emails
- Data Processing Agreement (DPA) available
- Transparency reports published annually

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Gmail | US company, US jurisdiction |
| Proton Mail | Swiss jurisdiction (still strong, but not EU) |
| Outlook.com | US company |
