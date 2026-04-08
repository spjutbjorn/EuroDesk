# Jitsi Meet

**Category:** Video Conferencing
**Type:** Self-hosted or managed
**Jurisdiction:** EU-hostable
**Website:** [jitsi.org](https://jitsi.org)

## What It Is

Jitsi Meet is a fully open-source, browser-based video conferencing platform. No account required to join a meeting. It replaces Zoom, Google Meet, and Microsoft Teams for video calls.

## EU Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Deploy on any EU VPS — full control |
| **8x8.vc (Jitsi as a Service)** | Managed, check data residency before use |
| **Infomaniak kMeet** | Swiss-hosted, based on Jitsi |
| **Framatalk** | French-hosted free instance (framatalk.org) |

## Setup (Self-hosted)

### Requirements
- Ubuntu 22.04 server
- Domain with DNS pointing to the server
- Ports 80, 443, 10000/UDP open

### Install

```bash
# Add Jitsi repository
curl https://download.jitsi.org/jitsi-key.gpg.key | sudo sh -c 'gpg --dearmor > /usr/share/keyrings/jitsi-keyring.gpg'
echo 'deb [signed-by=/usr/share/keyrings/jitsi-keyring.gpg] https://download.jitsi.org stable/' | sudo tee /etc/apt/sources.list.d/jitsi-stable.list

sudo apt update
sudo apt install jitsi-meet
```

During installation you will be prompted for:
- Your hostname (e.g., `meet.your-company.eu`)
- SSL certificate — choose "Let's Encrypt" for automatic HTTPS

### Post-install: Lock Down Room Creation

Edit `/etc/prosody/conf.avail/your-hostname.cfg.lua`:

```lua
VirtualHost "your-hostname"
    authentication = "internal_hashed"  -- require login to create rooms
```

Then create host accounts:

```bash
sudo prosodyctl register admin meet.your-company.eu yourpassword
```

### Enable Lobby (Waiting Room)

In `/etc/jitsi/meet/your-hostname-config.js`:

```javascript
lobbyEnabled: true,
```

### Firewall

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 10000/udp
sudo ufw allow 3478/udp
sudo ufw allow 5349/tcp
```

### Start Services

```bash
sudo systemctl enable --now jitsi-videobridge2 jicofo prosody nginx
```

## Docker Compose Alternative

```yaml
version: '3'
services:
  web:
    image: jitsi/web:stable
    ports:
      - "80:80"
      - "443:443"
    environment:
      - PUBLIC_URL=https://meet.your-company.eu
      - ENABLE_LETSENCRYPT=1
      - LETSENCRYPT_DOMAIN=meet.your-company.eu
      - LETSENCRYPT_EMAIL=admin@your-company.eu
```

See the full [docker-jitsi-meet](https://github.com/jitsi/docker-jitsi-meet) repo for the complete compose file.

## Key Features

- No account required to join (share a link)
- Screen sharing, backgrounds, recording
- Lobby/waiting room
- Password-protected rooms
- Works entirely in-browser (no install for participants)
- Mobile apps (iOS, Android)
- YouTube live streaming

## Compliance Notes

- Self-hosted: all meeting data stays on your server
- No telemetry to third parties when self-hosted
- Recordings stored locally or to your own S3-compatible storage
- GDPR: no user data collected beyond what you configure

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Zoom | US-hosted, data processed in USA |
| Google Meet | US company, data not EU-resident |
| Microsoft Teams | Complex, heavy; EU residency requires E3+ licensing |
