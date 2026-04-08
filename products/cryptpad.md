# CryptPad

**Category:** Collaborative Documents (End-to-End Encrypted)
**Type:** Self-hosted or managed
**Jurisdiction:** France (EU, GDPR) — flagship instance hosted by XWiki SAS, Paris
**Website:** [cryptpad.org](https://cryptpad.org)

## What It Is

CryptPad is a zero-knowledge, end-to-end encrypted collaborative office suite. It includes a rich-text editor, spreadsheets, presentations, kanban boards, whiteboards, code pads, and forms — all with real-time collaboration and without the server ever seeing your content.

## EU Hosting Options

| Option | Description |
|---|---|
| **cryptpad.fr** | Official managed instance, Paris, France |
| **Self-hosted** | Run on any EU server |
| **Community instances** | Various EU-hosted community instances |

## Plans (cryptpad.fr managed)

| Plan | Price | Storage |
|---|---|---|
| **Guest** | Free | 50 MB (non-persistent) |
| **Registered (free)** | Free | 1 GB |
| **Individual** | 5 €/mo | 10 GB |
| **Micro** | 10 €/mo | 25 GB |
| **Standard** | 15 €/mo | 100 GB |
| **Crystal** | 30 €/mo | 1 TB |

## Self-Hosted Setup

### Requirements
- Node.js 14+
- nginx
- A domain name

### Install

```bash
# Clone the repository
git clone https://github.com/cryptpad/cryptpad.git
cd cryptpad

# Install dependencies
npm install

# Copy configuration
cp config/config.example.js config/config.js
```

### Configure `config/config.js`

```javascript
module.exports = {
    httpUnsafeOrigin: 'https://pad.your-company.eu',
    httpSafeOrigin: 'https://pad-sandbox.your-company.eu',

    adminKeys: [
        // Add your public signing key here after first login
    ],

    filePath: './datastore/',
    archivePath: './data/archive',
    pinPath: './data/pins',
    taskPath: './data/tasks',
    blockPath: './block',
    blobPath: './blob',
    blobStagingPath: './data/blobstage',

    // Restrict registration to invite-only
    restrictRegistration: true,

    // Disable anonymous usage (recommended for office use)
    allowSubscriptions: false,
};
```

### nginx Configuration

CryptPad requires **two** domains — one for the main app and one for the sandbox iframe:

```nginx
server {
    listen 443 ssl;
    server_name pad.your-company.eu;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

server {
    listen 443 ssl;
    server_name pad-sandbox.your-company.eu;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
    }
}
```

### Run with systemd

```ini
[Unit]
Description=CryptPad
After=network.target

[Service]
User=cryptpad
WorkingDirectory=/opt/cryptpad
ExecStart=/usr/bin/node server.js
Restart=always

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl enable --now cryptpad
```

## Document Types

| Type | Description |
|---|---|
| **Rich Text** | Collaborative word processor |
| **Spreadsheet** | Excel-compatible (OnlyOffice engine) |
| **Presentation** | PowerPoint-compatible (OnlyOffice engine) |
| **Code** | Syntax-highlighted code editor |
| **Kanban** | Task boards |
| **Whiteboard** | Drawing and diagrams |
| **Form** | Surveys with encrypted responses |
| **Markdown** | Lightweight text with preview |

## Key Features

- Zero-knowledge E2E encryption: the server never sees content
- Real-time collaboration (multiple users simultaneously)
- No account required to view/edit shared documents
- Document ownership and access control
- Password-protected documents
- Drive for organizing all your pads
- Teams with shared drives and permissions

## Compliance Notes

- Servers in France (EU GDPR)
- Zero-knowledge design: even a compromised server cannot read content
- No analytics or tracking on self-hosted instances
- Open source (AGPL-3.0)
- GDPR: users can delete all their data; server admin can purge accounts

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Google Docs | US company, Google reads your documents |
| Notion | US company, data not EU-resident |
| Microsoft Office Online | US company |
