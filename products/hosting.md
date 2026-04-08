# EU Hosting Providers

**Category:** Cloud Infrastructure, GPU Hosting, AI Inference
**Type:** IaaS / PaaS
**Jurisdiction:** EU-ägda bolag, data stannar i EU
**Website:** [hetzner.com](https://www.hetzner.com)

## Hosting Options

| Option | Description |
|---|---|
| **EU-owned infrastructure providers** | Run the rest of the EuroDesk stack on EU- or adequacy-country-owned hosting |

## Generell molninfrastruktur

| Leverantör | Land | Styrka |
|---|---|---|
| **Hetzner** | Tyskland/Finland | Billigt, pålitligt, populärt för dev |
| **OVHcloud** | Frankrike | 30+ datacenter, stor EU-aktör |
| **Scaleway** | Frankrike | Tekniskt kapabelt, Paris/Amsterdam/Warszawa |
| **IONOS** | Tyskland | Enterprise, backar Euro-Office |
| **UpCloud** | Finland | ISO 27001, nordisk |
| **Exoscale** | Schweiz | Datalokalisering per region |
| **STACKIT** | Tyskland | Schwarz Group (Lidl-ägarna), enterprise |
| **Open Telekom Cloud** | Tyskland | T-Systems/Deutsche Telekom |

## GPU / AI-hosting

| Leverantör | Land | GPU:er |
|---|---|---|
| **Genesis Cloud** | Europa | H100, H200, B200 — GPU-first |
| **Verda** (f.d. DataCrunch) | Norden | 100% förnybar energi, GDPR |
| **Exoscale** | Schweiz | A30, V100, A40 m.fl. |
| **OVHcloud** | Frankrike | H100, L40S, V100S |
| **Nebius** | Europa | Stora GPU-kluster, InfiniBand |

## Marketplace-modell (EU-noder)

| Leverantör | Beskrivning |
|---|---|
| **Vast.ai** | Många EU-hostar (DE, NL, FI, SE, FR), ofta 10-20% billigare |
| **RunPod** | Amsterdam-region |

## Viktigt: GDPR vs suveränitet

GDPR-compliance ≠ suveränitet. För verklig suveränitet krävs att leverantörens juridiska enhet är EU-ägd — annars kan US CLOUD Act tvinga fram dataåtkomst även om servrarna står i EU.

**Fullt suveräna:** Hetzner, OVHcloud, Scaleway, IONOS, STACKIT, UpCloud, Exoscale, Open Telekom Cloud

**Ej suveräna (US-ägda med EU-regioner):** AWS, Azure, GCP — data kan nås via CLOUD Act oavsett serverplacering.

## Compliance Notes

- För managed drift bör leverantören vara EU-ägd eller ligga i ett adequacy-godkänt land.
- Undvik US-ägda hyperscalers för känsliga arbetslaster även om regionen ligger i EU.
- Dokumentera datalagring, underbiträden och backup-lokalisering för varje vald hostingleverantör.
