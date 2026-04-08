# EuroDesk Inclusion Rules

To be included in the EuroDesk stack, a product must meet strict criteria regarding data privacy, legal jurisdiction, and operational sovereignty.

## 1. Primary Jurisdiction Rule
The product or service provider must operate under one of the following:
- **EU/EEA Member States:** Fully subject to the GDPR.
- **Adequacy-Approved Countries:** Countries with a formal "Adequacy Decision" from the European Commission (e.g., Switzerland), where local laws provide equivalent protection to the GDPR.

## 2. The Sovereignty Rule (Anti-CLOUD Act)
To ensure full protection from foreign government access:
- **Preferred:** The parent company and its technical operations are headquartered and registered within the EU/EEA.
- **Mandatory for Managed SaaS:** Data must be stored and processed exclusively on servers within the EU/EEA, owned by an EU-based legal entity (e.g., Hetzner, OVHcloud, Scaleway).
- **Prohibited:** US-owned cloud regions (AWS, Azure, GCP) do not qualify for "managed" status due to the US CLOUD Act, which can compel US companies to provide data access regardless of server location.

## 3. The Self-Hosting Exception
Tools developed by companies outside the EU (e.g., USA) may be included **ONLY IF**:
- They are **Open Source** or **Source-Available**.
- They can be fully **Self-Hosted** on EU-owned infrastructure.
- The guide for the tool explicitly includes instructions to disable all non-EU telemetry, "phone-home" beacons, and external analytics.

## 4. Privacy & Technical Standards
- **Zero-Knowledge / E2E Encryption:** Preferred for high-sensitivity tools (Password managers, E-mail, Cloud storage).
- **No-Log Policy:** Mandatory for network-level tools (VPNs).
- **GDPR Compliance:** Must support data export, deletion, and local audit trails.
- **Transparency:** Open-source software is preferred to allow for independent security and privacy audits.

## 5. Documentation Requirements
Each product guide must clearly state:
- **Category & Type** (SaaS vs. Self-hosted).
- **Jurisdiction** of the provider.
- **Hosting Options** that satisfy the above rules.
- **Compliance Notes** explaining how to avoid common privacy pitfalls.
