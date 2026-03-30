# Nationale Vacaturebank Scraper

Extract structured job data from [nationalevacaturebank.nl](https://nationalevacaturebank.nl) — the Netherlands' second-largest job portal with 100K+ listings.

**[Use this actor on Apify](https://apify.com/blackfalcondata/nationalevacaturebank-scraper)**

## What does Nationale Vacaturebank Scraper do?

Nationale Vacaturebank Scraper extracts structured job data from [nationalevacaturebank.nl](https://nationalevacaturebank.nl) — including salary data, contact details, company metadata, full descriptions, and location data. It supports keyword search, location filters, and controllable result limits, so you can run the same query consistently over time. The actor also offers detail enrichment (full descriptions, company metadata, and contact information) where the source provides them, incremental monitoring that only returns new or changed results on recurring runs, and a compact output mode for AI-agent and MCP workflows.

## What data can you extract from nationalevacaturebank.nl?

Each result includes Core listing fields (`jobId`, `title`, `city`, `province`, `municipality`, `postalCode`, `latitude`, and `longitude`, and more), detail fields when enrichment is enabled (`description`), contact and apply information (`contactEmail`, `contactPhone`, and `directApply`), and company metadata (`company`, `companyType`, and `companyWebsite`). In standard mode, all fields are always present — unavailable data points are returned as `null`, never omitted. In compact mode, only core fields are returned.

Enable detail enrichment in the input to get richer fields such as full descriptions, company metadata, and contact information where the source provides them.

## Input

The main inputs are a search keyword, an optional location filter, and a result limit. Additional filters and options are available in the input schema.

Key parameters:

- **`query`** — Job title or keyword (e.g. 'software developer', 'verpleegkundige').
- **`location`** — City name (e.g. 'Amsterdam', 'Rotterdam'). Currently used for logging — site filters by function title.
- **`contractType`** — Filter by contract type.
- **`educationLevel`** — Filter by required education level.
- **`careerLevel`** — Filter by career level.
- **`maxResults`** — Maximum total results (0 = unlimited). (default: `25`)
- **`includeDetails`** — Fetch detail pages for employment type and direct-apply status. Slower but adds extra fields. (default: `true`)
- **`descriptionMaxLength`** — Truncate description HTML to N chars. 0 = no truncation. (default: `0`)
- **`compact`** — Core fields only (for AI-agent/MCP workflows). (default: `false`)
- **`incrementalMode`** — Only emit new and changed listings compared to previous run. (default: `false`)
- **`stateKey`** — Stable identifier for tracked universe. Required when incrementalMode is true.

### Input example

```json
{
  "query": "software developer",
  "maxResults": 5,
  "includeDetails": true,
  "descriptionMaxLength": 0,
  "compact": false,
  "incrementalMode": false
}
```

## Output

Each run produces a dataset of structured job records. Results can be downloaded as JSON, CSV, or Excel from the Dataset tab in Apify Console.

### Example job record

```json
{
  "jobId": "ace473d3adf7c9fe426a34903ec2c022c608e5ddf4d885f47405595d48d9a953",
  "title": "Outsystems developer",
  "company": "Hoofdkantoor DMG",
  "companyType": "direct_employer",
  "companyWebsite": "https://www.mandemakers.nl/",
  "contactEmail": "t.vantent@dmg.eu",
  "contactPhone": null,
  "city": "Waalwijk",
  "province": "Noord-Brabant",
  "municipality": "WAALWIJK",
  "postalCode": "5145 RA",
  "latitude": "51.699209",
  "longitude": "5.053630",
  "country": "NL",
  "salaryMin": 3500,
  "salaryMax": 5848,
  "salaryType": "monthly",
  "salaryFormatted": "€3.500 - €5.848",
  "contractType": "Vast",
  "educationLevel": "HBO",
  "careerLevel": "Ervaren",
  "workingHoursMin": 1,
  "workingHoursMax": 40,
  "employmentType": [
    "FULL_TIME",
    "PART_TIME"
  ],
  "industries": [
    "Automatisering/Internet"
  ],
  "categories": [
    "Automatisering/Internet"
  ],
  "description": "<p>Jij werkt aan software waar collega's elke dag blij van worden! Dankzij jouw IT-skills maken we complexe bedrijfsprocessen efficiënter voor de collega's op onze hoofdkantoren en in de winkels. Soll...",
  "publishDate": "2026-03-11T23:00:00Z",
  "expiryDate": "2026-05-28T22:00:00Z",
  "portalUrl": "https://www.nationalevacaturebank.nl/vacature/8d24eff0-a64e-443b-9039-eb83115a45c5/outsystems-developer",
  "directApply": true,
  "scrapedAt": "2026-03-30T10:33:14.627Z",
  "source": "nationalevacaturebank.nl",
  "changeType": "NEW"
}
```

## How to scrape nationalevacaturebank.nl

1. Go to [Nationale Vacaturebank Scraper](https://apify.com/blackfalcondata/nationalevacaturebank-scraper) in Apify Console.
2. Enter a search keyword and optional location filter.
3. Set `maxResults` to control how many results you need.
4. Enable `includeDetails` if you need full descriptions, contact info, or company data.
5. Click **Start** and wait for the run to finish.
6. Export the dataset as JSON, CSV, or Excel.

## Use cases

- Extract job data from nationalevacaturebank.nl for market research and competitive analysis.
- Track salary trends across regions and categories over time.
- Monitor new and changed listings on scheduled runs without processing the full dataset every time.
- Build outreach lists using contact details and apply URLs from listings.
- Research company hiring patterns, employer profiles, and industry distribution.
- Use structured location data for regional analysis, mapping, and geo-targeting.
- Feed structured data into AI agents, MCP tools, and automated pipelines using compact mode.
- Export clean, structured data to dashboards, spreadsheets, or data warehouses.

## How much does it cost to scrape nationalevacaturebank.nl?

Nationale Vacaturebank Scraper uses pay-per-event pricing on Apify:

- **$0.01** per actor start
- **$0.002** per result

You only pay for what you use. There are no subscriptions or minimum fees.

## FAQ

### How many results can I get from nationalevacaturebank.nl?

The number of results depends on the search query and available listings on nationalevacaturebank.nl. Use the `maxResults` parameter to control how many results are returned per run.

### Does Nationale Vacaturebank Scraper support recurring monitoring?

Yes. Enable incremental mode to only receive new or changed listings on subsequent runs. This is ideal for scheduled monitoring where you want to track changes over time without re-processing the full dataset.

### Can I integrate Nationale Vacaturebank Scraper with other apps?

Yes. Nationale Vacaturebank Scraper works with Apify's [integrations](https://apify.com/integrations) to connect with tools like Zapier, Make, Google Sheets, Slack, and more. You can also use webhooks to trigger actions when a run completes.

### Can I use Nationale Vacaturebank Scraper with the Apify API?

Yes. You can start runs, manage inputs, and retrieve results programmatically through the [Apify API](https://docs.apify.com/api/v2). Client libraries are available for JavaScript, Python, and other languages.

### Can I use Nationale Vacaturebank Scraper through an MCP Server?

Yes. Apify provides an [MCP Server](https://apify.com/apify/actors-mcp-server) that lets AI assistants and agents call this actor directly. Use compact mode and `descriptionMaxLength` to keep payloads manageable for LLM context windows.

### Is it legal to scrape nationalevacaturebank.nl?

This actor extracts publicly available data from nationalevacaturebank.nl. Web scraping of public information is generally considered legal, but you should always review the target site's terms of service and ensure your use case complies with applicable laws and regulations, including GDPR where relevant.

### Your feedback

If you have questions, need a feature, or found a bug, please [open an issue](https://apify.com/blackfalcondata/nationalevacaturebank-scraper/issues) on the actor's page in Apify Console. Your feedback helps us improve.

## You might also like

- [Adzuna Job Scraper](https://apify.com/blackfalcondata/adzuna-scraper) — Scrape adzuna.com — the global job board with 20+ country markets. Structured salary.
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper) — Scrape arbeitsagentur.de — Germany's official employment portal with 1M+ listings. Contact data, contract types, and remote work filters.
- [Bayt.com Scraper](https://apify.com/blackfalcondata/bayt-scraper) — Scrape bayt.com — the leading Middle East job board. Salary data, experience requirements.
- [Dice.com Job Scraper](https://apify.com/blackfalcondata/dice-com-job-scraper) — Scrape dice.com — the leading U.S. tech job board. Structured salary (min/max/currency).
- [Drushim Scraper](https://apify.com/blackfalcondata/drushim-scraper) — Scrape drushim.co.il — Israel's leading job board. Salary data, geo-coordinates, and multi-filter search.
- [Duunitori Scraper](https://apify.com/blackfalcondata/duunitori-scraper) — Scrape duunitori.fi — Finland's largest job board with 22,000+ listings. Salary ranges, employment types.
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper) — Scrape glassdoor.com across 21 markets. Salary data, employer ratings, and search filters.
- [Greenhouse Scraper](https://apify.com/blackfalcondata/greenhouse-scraper) — Scrape Greenhouse-powered career sites. Salary data, application questions, and department/office filters.
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper) — Scrape indeed.com — the world's largest job board. Structured salary, remote filters, and contact data.
- [Jobindex Scraper](https://apify.com/blackfalcondata/jobindex-scraper) — Scrape jobindex.dk — Denmark's leading job board. Salary data and detailed company profiles.
- [Jobs.ch Scraper](https://apify.com/blackfalcondata/jobs-ch-scraper) — Scrape jobs.ch — Switzerland's leading job board. Salary ranges, canton filters, and employment types.
- [Reed Scraper](https://apify.com/blackfalcondata/reed-scraper) — Scrape reed.co.uk — the UK's largest job board with 300K+ listings. Salary, contact details, and remote filters.
- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper) — Scrape stepstone.de and 13 European country portals. Salary data, contact details, and location filters.
