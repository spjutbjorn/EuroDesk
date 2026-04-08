# Startpage

**Category:** Search Engine
**Type:** Managed SaaS
**Jurisdiction:** Netherlands (EU, GDPR)
**Website:** [startpage.com](https://www.startpage.com)

## What It Is

Startpage is a privacy-preserving search engine based in Amsterdam, Netherlands. It acts as a proxy to Google search results — you get Google-quality results without Google tracking you. Startpage does not store IP addresses, does not use tracking cookies, and does not create search profiles.

## How It Works

1. You search on Startpage
2. Startpage forwards your search to Google anonymously (as a proxy)
3. Google returns results to Startpage
4. Startpage returns results to you — without Google knowing who you are

This means you get Google results with zero personal data going to Google.

## Hosting Options

| Option | Description |
|---|---|
| **Startpage managed** | Managed search service operated from the Netherlands |

## Setup

### Set as Default Browser Search Engine

#### Firefox

1. Go to [startpage.com](https://www.startpage.com)
2. Click the search bar in Firefox
3. Click the magnifying glass → **"Add Startpage"**

Or manually:
- **Settings** → **Search** → **Add search engine**
- URL: `https://www.startpage.com/sp/search?q=%s`

#### Chrome / Chromium / Brave

- **Settings** → **Search engine** → **Manage search engines**
- Add custom search engine:
  - Name: `Startpage`
  - Keyword: `sp` (or `@startpage`)
  - URL: `https://www.startpage.com/sp/search?q=%s`

#### Edge

- **Settings** → **Privacy, search, and services** → **Address bar and search**
- **Manage search engines** → **Add**

#### Safari

- **Settings** → **Search** → **Search Engine** → (Startpage not natively listed)
- Use a browser extension or the Startpage mobile app

### Set as Default on Mobile

#### Firefox Mobile

- **Settings** → **Search** → **Search Engine** → Add/Select Startpage

#### iOS / Android (via Startpage app)

- Download the Startpage app from App Store / Play Store
- Use it as your default browser alternative

## Key Features

- Google-quality search results without Google tracking
- Anonymous View: open search results through Startpage's proxy (hides your IP from websites too)
- No search history stored
- No tracking cookies
- No personalized ads
- HTTPS everywhere
- Available in multiple languages and regions
- EU search results bias available (set region to your country)

## Anonymous View

Startpage's unique **Anonymous View** lets you visit websites anonymously — clicking a search result opens it through Startpage's proxy, hiding your IP from the destination site.

Look for the **Anonymous View** button next to each search result.

## Privacy Settings

On Startpage, click the settings gear icon to configure:
- **Region**: set to your EU country for localized results
- **Language**: set your preferred language
- **Theme**: light or dark
- **Results per page**: 10 or 20
- **Safe search**: on/off

Settings are stored in a URL parameter (no account needed, no cookie tracking).

## For Organizations

There is no enterprise license — Startpage is free to use and set as the default search engine company-wide via browser policy.

### Chrome / Edge Browser Policy (GPO or MDM)

```json
{
  "DefaultSearchProviderEnabled": true,
  "DefaultSearchProviderName": "Startpage",
  "DefaultSearchProviderSearchURL": "https://www.startpage.com/sp/search?q={searchTerms}"
}
```

## Compliance Notes

- Startpage B.V. is based in Amsterdam, Netherlands (EU)
- Subject to EU GDPR
- No personal data stored or processed
- EU Court of Justice adequacy decisions apply
- Privacy verified by EuroPriSe (European Privacy Seal)
- Independent audit by European privacy certification bodies

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Google | The entire problem — tracks everything |
| Bing | Microsoft, US jurisdiction |
| DuckDuckGo | US company (though strong privacy claims) |
| Qwant | French alternative (see separate guide) |
| Brave Search | US company, independent index |
