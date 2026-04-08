# Proton VPN

**Category:** VPN
**Type:** Managed SaaS
**Jurisdiction:** Switzerland (equivalent EU protection, FADP)
**Website:** [protonvpn.com](https://protonvpn.com)

## What It Is

Proton VPN is a no-log VPN service from the makers of Proton Mail. Based in Geneva, Switzerland, it is subject to Swiss privacy law (FADP) and benefits from Switzerland's strong neutrality and tradition of bank-level privacy protections.

## Plans

| Plan | Price | Devices | Servers |
|---|---|---|---|
| **Free** | Free | 1 | Limited EU/US servers |
| **VPN Plus** | 6.99 €/mo (annual) | 10 | All servers |
| **Proton Unlimited** | 9.99 €/mo (annual) | 10 | All + all Proton apps |
| **Proton Business** | 7.99 €/user/mo | 10/user | All servers |
| **Proton Enterprise** | Custom | Custom | Custom |

## For Teams

Proton Business provides:
- Centralized billing
- Admin panel to manage user accounts
- Proton Mail, Calendar, and Drive included

### Setup for a Business Team

1. Go to [proton.me/business](https://proton.me/business)
2. Create an organization
3. Invite team members
4. Users download the VPN client and log in with their Proton account

## Client Installation

### Desktop (Windows, macOS, Linux)

Download from [protonvpn.com/download](https://protonvpn.com/download)

### Linux CLI

```bash
# Ubuntu/Debian
sudo apt install protonvpn-stable-release
sudo apt update && sudo apt install proton-vpn-gnome-desktop

# Or use the CLI version
sudo apt install protonvpn-cli
```

### CLI Usage

```bash
# Log in
protonvpn-cli login your@email.com

# Connect to fastest EU server
protonvpn-cli connect --fastest --cc CH

# Connect to specific country
protonvpn-cli connect --cc DE   # Germany
protonvpn-cli connect --cc SE   # Sweden

# Enable kill switch
protonvpn-cli killswitch --on

# Status
protonvpn-cli status
```

## Key Features

- No-log policy (audited by SEC Consult)
- Secure Core: route through Switzerland/Iceland/Sweden before exit
- NetShield (DNS-level ad and malware blocking)
- WireGuard, OpenVPN, and IKEv2 support
- Kill switch
- Split tunneling
- Stealth protocol (for restrictive networks)
- Port forwarding (P2P servers)
- Tor over VPN (Onion servers)
- Open source clients (all platforms)

## Secure Core (Double VPN)

Proton VPN's unique **Secure Core** routes your traffic through a hardened server in Switzerland, Iceland, or Sweden before reaching the exit server. This protects against endpoint compromise.

Enable in the app: **Connection** → **Secure Core** → **ON**

This is particularly valuable for high-sensitivity connections.

## NetShield (Ad/Malware Blocking)

In the app: **Connection settings** → **NetShield** → choose:
- **Block malware only**
- **Block malware, ads, and trackers** (recommended)

## VPN Accelerator

Proton VPN's proprietary performance improvement for WireGuard. Enable under **Settings** → **Advanced** → **VPN Accelerator** → **ON**. Significantly improves speeds on long-distance servers.

## Integration with Proton Ecosystem

If your team already uses Proton Mail, enabling Proton VPN means:
- Single sign-on with Proton account
- Unified billing
- Proton Drive, Calendar included (Proton Unlimited)
- Consistent privacy umbrella across services

## Compliance Notes

- Based in Geneva, Switzerland
- Swiss FADP provides equivalent protection to EU GDPR
- No-log policy independently audited (SEC Consult, 2023)
- Open-source clients allow independent verification
- No US CLOUD Act exposure
- Proton AG is employee-owned, no VC pressure to monetize data

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Mullvad | Swedish/EU-based, excellent privacy (see separate guide) |
| NordVPN | Panama-based, owned by investment group |
| ExpressVPN | Acquired by Kape Technologies |
| Commercial "privacy" VPNs | Many have opaque ownership, US ties |
