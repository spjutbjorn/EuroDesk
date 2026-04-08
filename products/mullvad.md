# Mullvad VPN

**Category:** VPN
**Type:** Managed SaaS
**Jurisdiction:** Sweden (EU, GDPR)
**Website:** [mullvad.net](https://mullvad.net)

## What It Is

Mullvad is a privacy-focused VPN provider based in Gothenburg, Sweden. It is widely regarded as one of the most privacy-respecting VPN services in the world — no email required to sign up, no usage logs, audited independently.

## Hosting Options

| Option | Description |
|---|---|
| **Mullvad managed** | Managed VPN service operated by a Swedish provider |

## Pricing

| Plan | Price |
|---|---|
| **Standard** | 5 €/month (same for all) |

No tiered pricing, no upsells. One flat rate per device license.

## For Teams

Mullvad does not have a traditional "team dashboard." Each user manages their own account independently. You can:
- Purchase multiple account licenses (each is a number, no email needed)
- Distribute licenses to team members
- Each license allows 5 simultaneous devices

## Setup

### Install the Client

Download from [mullvad.net/download](https://mullvad.net/download):
- Windows, macOS, Linux (desktop app)
- iOS and Android (mobile app)

### Connect

1. Open the Mullvad app
2. Enter your 16-digit account number
3. Select a server (choose an EU server for EU IP)
4. Click **Connect**

### Linux (CLI)

```bash
# Install on Debian/Ubuntu
sudo apt install mullvad-vpn

# Add account
mullvad account login 1234123412341234

# Set server to Sweden
mullvad relay set location se

# Connect
mullvad connect

# Check status
mullvad status
```

### Server Selection for EU-Only Traffic

To ensure traffic always routes through EU servers:

In the app: **Settings** → **VPN settings** → **Tunnel protocol**: WireGuard → **Server** → Filter by country (Sweden, Germany, Netherlands, etc.)

Or via CLI:
```bash
# List EU countries
mullvad relay list | grep -E "^(de|se|nl|fr|fi|no|dk|at|ch|be|es|it|pl)"

# Set to Germany (Frankfurt)
mullvad relay set location de fra
```

## Key Features

- No-log policy (independently audited by Cure53)
- No email or personal info required
- WireGuard and OpenVPN support
- DAITA (Defense Against AI-guided Traffic Analysis) — unique feature
- Multihop (route through two servers)
- Kill switch (blocks traffic if VPN drops)
- Split tunneling
- DNS-based ad/tracker blocking built-in
- Supports Bitcoin and cash payments for extra anonymity
- IPv6 support

## Split Tunneling (Work Exemptions)

Allow specific apps to bypass the VPN (e.g., if internal resources require direct connection):

In the app: **Settings** → **Split tunneling** → Add apps to bypass

```bash
# CLI
mullvad split-tunnel add /usr/bin/some-app
```

## Kill Switch

Ensure no traffic leaks if VPN disconnects:

In the app: **Settings** → **VPN settings** → **Always require VPN**

```bash
mullvad lockdown-mode set on
```

## DNS Settings

Mullvad offers encrypted DNS (DoH/DoT) with optional filtering:

**Settings** → **DNS settings**:
- **Block ads** — filters ad domains
- **Block trackers** — filters tracker domains
- **Block malware** — filters malware domains

## Compliance Notes

- Based in Sweden, subject to EU GDPR
- No-log policy audited by Cure53 (2020, 2021) and Assured AB
- Sweden does not have mandatory data retention laws for VPNs
- Mullvad's infrastructure does not link connections to accounts
- Warrant canary published

## Alternatives Considered

| Alternative | Why not |
|---|---|
| NordVPN | Panama-based, marketing-heavy |
| ExpressVPN | Acquired by Kape Technologies (US-linked) |
| ProtonVPN | Swiss, strong alternative (see separate guide) |
| Surfshark | Netherlands + US ties |
