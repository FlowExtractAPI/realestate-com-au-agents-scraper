**[realestate.com.au Agents & Agencies Scraper](https://apify.com/dz_omar/realestate-com-au-agents-scraper?fpr=smcx63)** turns a **suburb, a postcode or any realestate.com.au search URL** into a clean directory of **real estate agents and agencies** — with **email and phone**, the agency, listings for sale and for rent, recent sales, **median sold price** and the suburbs each agent is active in.

Perfect for **real estate CRMs and lead generation**, **recruiters** shortlisting top producers, **proptech and portals** building agent databases, and **market researchers** mapping who is active where.

## What does realestate.com.au Agents & Agencies Scraper do?

- **Two ways in** — list suburbs (`Sydney, NSW, 2000`) or paste realestate.com.au search URLs.
- **Contacts on every agent** — primary email plus every published address, mobile and office phone.
- **Performance signals** — for-sale, for-rent and recently-sold counts, median sold price, last sold date, active suburbs and property types.
- **Agency records** — optional: contacts, the full team roster seen, agent count and listing counts.
- **Each agent and agency once** — returned and charged once per run, however many listings they appear on.

### What data can you extract from realestate.com.au agents?

| Field | Description |
|---|---|
| `name`, `jobTitle` | Agent name and role |
| `email`, `emails` | Primary email plus every published email address |
| `phone`, `mobile`, `officePhone` | Contact numbers |
| `agency` | The agent's agency: name, phone, email, website, address, profile link, logo |
| `stats.listingsForSale` / `listingsForRent` / `recentlySold` | Current and recent activity counts |
| `stats.medianSoldPrice` | Median of the agent's recent sold prices (AUD) |
| `stats.lastSoldDate` | Date of their most recent sale |
| `stats.activeSuburbs` | Suburbs the agent is currently active in |
| `stats.propertyTypes` | Property types they handle |
| `profileUrl`, `photo` | realestate.com.au profile link and headshot |
| `sampleListings` | A few of the agent's current/recent listings for context |

**Agency records (optional):** name, email(s), phone, website, office address, suburb/state/postcode, profile link, logo, the **full team roster** of agents seen, `agentCount`, and listing counts (for sale / for rent / sold) with a median sold price.

### Why scrape realestate.com.au agents?

realestate.com.au is Australia's largest property portal, and behind every listing is the agent marketing it — the most complete public picture of who is selling and leasing in any suburb right now.

- **Lead generation** — contact lists of agents actively listing in your target suburbs.
- **Recruitment & talent scouting** — rank agents by properties sold, median sold price and activity.
- **CRM enrichment** — match agents and agencies to current activity and contact details.
- **Agency intelligence** — a whole agency's team roster with for-sale / for-rent / sold counts.
- **Market mapping** — which agents and agencies dominate a suburb or region.

### Why use it on Apify?

Running it on Apify gives you **API access**, **scheduling**, **monitoring**, **integrations** (Make, Zapier, n8n, webhooks) and **proxy rotation** without managing infrastructure.

## How to scrape realestate.com.au agents

1. Open [realestate.com.au Agents & Agencies Scraper](https://apify.com/dz_omar/realestate-com-au-agents-scraper?fpr=smcx63) in Apify Console.
2. Choose **Mode**: `location` (list suburbs) or `url` (paste search URLs).
3. Enter **Locations** as `Suburb, STATE, Postcode`, or paste **Search URLs**.
4. Pick **Listing types to search** (`buy`, `rent`, `sold`), turn on **Also return agencies** if needed, and set **Max agents** (start small: `50`).
5. Click **Start**, then download the results as JSON, CSV or Excel, or fetch them over the API.

## How much does it cost to scrape realestate.com.au agents?

You pay per record returned:

| Event | FREE | BRONZE | SILVER | GOLD |
|---|---|---|---|---|
| Agent record | $0.0018 | $0.0015 | $0.0013 | $0.0011 |
| Agency record (when *Also return agencies* is on) | $0.0018 | $0.0015 | $0.0013 | $0.0011 |

- **1,000 agents** cost about **$1.80** on the FREE plan price and **$1.10** on GOLD.
- Cap any run with the **maximum cost per run** setting; test with `maxAgents: 10` first.

## Input and output examples

### Input — by location

```json
{
  "mode": "location",
  "locations": ["Sydney, NSW, 2000", "Richmond, VIC, 3121"],
  "channels": ["buy", "rent", "sold"],
  "includeAgencies": true,
  "maxAgents": 50
}
```

### Input — by search URL

```json
{
  "mode": "url",
  "startUrls": [
    { "url": "https://www.realestate.com.au/buy/in-sydney,+nsw+2000/list-1" }
  ],
  "maxAgents": 100
}
```

| Option | Description |
|---|---|
| **Mode** | `location` (list suburbs) or `url` (paste search URLs). Fields for the other mode are ignored. |
| **Locations** | location mode — areas as `Suburb, STATE, Postcode` (postcode optional). |
| **Listing types to search** | Both modes — `buy`, `rent`, `sold` (default all). `sold` adds real sold-price stats. In url mode each URL runs as pasted, and the same area is also searched for the other selected types (price filters aren't carried over). |
| **Include surrounding suburbs** | location mode — also include neighbouring suburbs. |
| **Search URLs** | url mode — realestate.com.au search URLs. |
| **Also return agencies** | One record per agency, with its team roster and counts. |
| **Max agents** | Stop after this many agents (`0` = all found). Agencies are returned in addition. |
| **Max pages per search** | How deep to scan each search (up to 100 listings per page). More pages = more agents and fuller stats. |

### Output

```json
{
  "recordType": "agent",
  "agentId": "2884534",
  "name": "Sample Agent",
  "jobTitle": "Director/Sales Agent",
  "email": "agent@example-realty.com.au",
  "emails": ["agent@example-realty.com.au", "capture@example-realty.agentboxmail.com.au"],
  "phone": "0400000000",
  "mobile": "0400000000",
  "officePhone": "03 0000 0000",
  "agency": {
    "id": "AAA000",
    "name": "Example Realty",
    "phone": "03 0000 0000",
    "email": "office@example-realty.com.au",
    "website": "https://www.example-realty.com.au",
    "address": "1 High Street, Sampletown, VIC 3000",
    "profileUrl": "https://www.realestate.com.au/agency/example-realty-AAA000",
    "logo": "https://.../logo.jpg"
  },
  "stats": {
    "listingsForSale": 21,
    "listingsForRent": 0,
    "recentlySold": 30,
    "totalListings": 51,
    "medianSoldPrice": 675000,
    "lastSoldDate": "2026-09-16",
    "activeSuburbs": ["Sampletown"],
    "propertyTypes": ["house", "unit"]
  },
  "profileUrl": "https://www.realestate.com.au/agent/2884534",
  "source": "realestate.com.au",
  "scrapedAt": "2026-01-01T00:00:00.000Z"
}
```

Values above are illustrative placeholders, not a real record.

## Other Actors you might need

<!-- RECOMMENDED:START (generated by apify-actor-forge/tools/recommend.py; edits inside are overwritten) -->

| Actor | What it adds |
|---|---|
| **[realestate.com.au Scraper](https://apify.com/dz_omar/realestate-com-au-scraper?fpr=smcx63)** | Buy, rent & sold listings from any search URL with agent contacts, inspections & photos |
| **[Domain.com.au Scraper](https://apify.com/dz_omar/domain-scraper?fpr=smcx63)** | Australian listings with agent contacts, nearby schools, market insights & floor plans |
| **[realcommercial.com.au Scraper](https://apify.com/dz_omar/realcommercial-com-au-scraper?fpr=smcx63)** | Sold, Leased & Agent Phones |
| **[Idealista Scraper API](https://apify.com/dz_omar/idealista-scraper-api?fpr=smcx63)** | Any Search URL, No Result Cap & France |
| **[California Business & UCC Lien Search](https://apify.com/dz_omar/california-bizfile-scraper?fpr=smcx63)** | California business entities & UCC liens: status, registered agent and filings |

<!-- RECOMMENDED:END -->

## Frequently asked questions

### How are agents and their stats built?

The Actor walks the live listings for your locations (or URLs) across the buy, rent and sold channels and assembles one record per agent and per agency from the people marketing those properties. Counts, median sold price and active suburbs are computed from the listings scanned in that run — so a higher **Max pages per search** gives richer stats in large suburbs.

### Are the stats a full census?

No — a sample. Stats describe **the listings scanned in that run**. Each search is scanned up to **Max pages per search** (100 listings per page), and realestate.com.au serves at most 2,000 results per search, so a single nationwide URL sees only a slice; an agency with dozens of offices may appear with a handful. The run log warns whenever a search stops before its last result. For broad coverage, use location mode with many suburbs (each suburb × listing type is its own search), or paste many narrower URLs.

### Why don't agent totals add up to agency totals?

A listing marketed by two agents is credited to **both** agents, so summing agent counts counts it twice. Agency counts credit each listing **once**. To total by agency, franchise group or area, use the agency records.

### Why did I get fewer results than expected?

| Situation | What you see | What to do |
|---|---|---|
| A pasted URL isn't a recognized realestate.com.au URL | Skipped, with a note in the run log | Copy the URL directly from your browser |
| A location entry can't be read | Skipped, with a note in the run log | Use the `Suburb, STATE, Postcode` form |
| A suburb has fewer agents than `Max agents` | All the agents found | Add more suburbs/URLs, or raise *Max pages per search* |
| Nothing usable in the input | A single guidance item in the dataset | Add a location or a search URL |

### Do I need a realestate.com.au account?

No. The Actor reads publicly visible listings — no login and no cookies.

### Is it legal to use the contact details?

The data is publicly available, but you are responsible for using contact details lawfully — for example under the Australian Privacy Act and Spam Act: no spam or unsolicited bulk outreach. This is not legal advice.

### Can I use it in Make, Zapier, n8n or my own code?

Yes — through Apify's integrations, or with the Apify API and client libraries.

## Support

- 🌐 **Website:** [flowextractapi.com](https://flowextractapi.com)
- 📧 **Email:** [support@flowextractapi.com](mailto:support@flowextractapi.com)
- 💬 **GitHub:** [FlowExtractAPI](https://github.com/FlowExtractAPI)
- 💼 **LinkedIn:** [flowextract-api](https://www.linkedin.com/in/flowextract-api/)
- 🐦 **X (Twitter):** [@FlowExtractAPI](https://x.com/FlowExtractAPI)
- 📱 **Facebook:** [flowextractapi](https://www.facebook.com/flowextractapi)
- 🎵 **TikTok:** [@flowextractapi](https://www.tiktok.com/@flowextractapi)

## Legal & compliance

- **Public data only** — agent and agency data any visitor sees without logging in.
- **Rate limiting** — modest request rates with back-off; built for research and analysis.
- **Data protection** — no storage of personal information beyond your own run's dataset.
- **Commercial use** — suitable for business intelligence and research.
- No affiliation with or endorsement by realestate.com.au or REA Group is implied.

---

*realestate.com.au Agents & Agencies Scraper — by FlowExtract API. Turn any website into structured data.*
