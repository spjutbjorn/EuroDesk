# Qwant

**Category:** Search Engine
**Type:** Managed SaaS
**Jurisdiction:** France (EU, GDPR)
**Website:** [qwant.com](https://www.qwant.com)

## What It Is

Qwant is a French search engine headquartered in Paris, operating its own index (not a Google proxy). It is one of the few European search engines with a fully independent crawling infrastructure, making it the most "EU-native" search option. The French government has endorsed Qwant as the recommended browser for civil servants.

## Hosting Options

| Option | Description |
|---|---|
| **Qwant managed** | Managed search service operated from France |

## Qwant Products

| Product | Description |
|---|---|
| **Qwant** | Main web search |
| **Qwant Junior** | Child-safe filtered search |
| **Qwant Maps** | Privacy-respecting maps (OpenStreetMap) |
| **Qwant Business** | White-label and API access |

## Setup

### Set as Default Browser Search Engine

#### Firefox

1. Visit [qwant.com](https://www.qwant.com)
2. Click the address bar search engine icon → **Add Qwant**

Or manually in **Settings** → **Search** → Add:
- URL: `https://www.qwant.com/?q=%s`

#### Chrome / Chromium / Brave

**Settings** → **Search engine** → **Manage search engines** → **Add**:
- Name: `Qwant`
- Keyword: `q`
- URL: `https://www.qwant.com/?q=%s`

#### Edge

**Settings** → **Privacy, search, and services** → **Address bar and search** → **Manage search engines** → **Add**:
- Search engine: `Qwant`
- URL: `https://www.qwant.com/?q=%s`

#### Safari

No native integration. Use the search URL as a bookmark or use the Qwant browser extension.

### Mobile

- **iOS**: Available in Firefox for iOS as a search option; or use the Qwant app
- **Android**: Available as a search engine in Firefox; Qwant browser app available
- **DuckDuckGo browser** (Android/iOS) does not support Qwant natively, use Firefox instead

### For Organizations — Browser Policy (Chrome/Edge GPO)

```json
{
  "DefaultSearchProviderEnabled": true,
  "DefaultSearchProviderName": "Qwant",
  "DefaultSearchProviderSearchURL": "https://www.qwant.com/?q={searchTerms}&client=opensearch"
}
```

## Key Features

- Own search index (not a proxy to Google or Bing)
- No user tracking, no search profiles
- No personalized results (same results for everyone)
- No advertising based on search history
- EU-based infrastructure
- Qwant Maps: OpenStreetMap-based maps without Google/Apple tracking
- Social tab: Twitter/news results alongside web results
- News tab: aggregated EU and international news

## Qwant Maps

A privacy-respecting alternative to Google Maps, based on OpenStreetMap:

- [maps.qwant.com](https://maps.qwant.com)
- Directions, POI search, transit routes
- No account required
- No location tracking

## Limitations vs. Google

- Index coverage is smaller than Google
- Some niche technical queries return fewer results
- Image search is less comprehensive
- No Google Knowledge Graph-style cards

For better results on technical queries, Qwant blends its index with Bing results (with privacy protections applied).

## Compliance Notes

- Qwant SAS is incorporated in Paris, France
- Subject to French data protection law (CNIL) and EU GDPR
- Supervised by CNIL (Commission Nationale de l'Informatique et des Libertés)
- Endorsed by French government (ANSSI, BetaGouv)
- No cross-site tracking
- Certified as compliant by the French government for civil servant use

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Google | US company, extensive tracking |
| Bing | Microsoft, US company |
| DuckDuckGo | US company (though strong privacy) |
| Startpage | Netherlands-based, Google proxy (see separate guide) |
| Ecosia | German company, uses Bing — not a fully independent index |
