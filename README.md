# B2B Marketing Attribution Dashboard

An interactive, self-contained HTML dashboard for analyzing which marketing channels generate leads, create pipeline, and close revenue across multiple attribution models.

No coding required. No server needed. Just open the HTML file in any modern browser.

> **Note:** Always verify dashboard outputs against your source data. AI-assisted calculations should be double-checked before using in budget decisions or stakeholder reports.

---
![Attribution Dashboard](https://github.com/user-attachments/assets/8a3a75b7-a06f-46b1-a558-7395528986d4)

## What it does

Upload your CRM or marketing automation data as a CSV and get instant visibility into:

- **Which channels generate the most leads** — ranked by volume and MQL rate, with W-Shaped, U-Shaped, Linear, First Touch, and Last Touch attribution models
- **Which channels create pipeline** — SQL-to-opp conversion, pipeline value by source, and which channel touched each deal before it became an opportunity
- **Which channels close deals** — ARR by last touch, win rates, and average deal size by first-touch channel
- **Which channels nurture in the middle** — middle-touch frequency, distribution donut chart, and a first-touch → middle-touch heatmap
- **How fast each channel moves leads through your funnel** — median days per stage, lead-to-close by channel (only shown for channels with actual closed deals)
- **Full funnel shape** — visual funnel with proportional bar widths, stage drop-off rates, and lead-to-close rate by channel
- **Channel Scorecard** — sortable table with badges highlighting which channel wins each "job" (most leads, best pipeline rate, highest ARR, etc.)
- **Cost efficiency** — enter your actual monthly spend per channel (including labor, tools, and program costs) to calculate ROI, CPL, CP-MQL, CP-Opp, payback period, and pipeline coverage

All data stays in your browser. Nothing is sent anywhere.

---

## How to use it

1. Download `Attribution_Dashboard.html`
2. Open it in Chrome, Safari, Firefox, or Edge
3. Click **Use Sample Data** to explore with 2,000 fictional leads, or upload your own CSV
4. If uploading your own CSV, map your column names to the dashboard fields — the dashboard auto-detects most common naming conventions
5. Use the filters at the top to slice by industry, company size, or channel category
6. Switch attribution models using the Attribution Model dropdown to see how channel rankings change

---

## Preparing your data

Your CSV needs one row per lead or contact. Download `attribution_template.csv` to see the exact format.

### Required columns

| Column | What to put here |
|---|---|
| First Touch | The channel that first generated this lead (e.g. "Organic Search", "Paid Social") |
| Lead Created Date | When the lead was created |
| Pipeline Touch Channel | The channel present when this lead became an opportunity (leave blank if no opp) |
| Last Touch Before Close | The channel present when this deal closed (leave blank if not closed) |
| MQL Date | When the lead reached MQL status (leave blank if not yet MQL) |
| SQL Date | When the lead became SQL |
| Opp Created Date | When an opportunity was created from this lead |
| Close Date | When the deal closed (leave blank if not closed) |
| Deal Value (ARR) | Annual contract value in dollars — accepts `$175,000`, `175000`, or `175000.00` |
| Sales Stage | Current stage name (e.g. "Stage 3: Evaluation", "Closed Won") |
| Industry | The prospect's industry (e.g. "Tech", "Healthcare", "Financial Services") |
| Company Size | Employee count band (e.g. "1,000–5,000 employees") |

### Optional columns

| Column | What to put here |
|---|---|
| Middle Touch columns | Channels that touched this lead between first and last touch. Name these columns anything that starts with "Middle Touch", "Mid Touch", "Touch 1", "MT 1", "Nurture Touch", or "Engaging Touch" — the dashboard auto-detects them. There is no limit on the number of middle touch columns. |
| Is Won? | Whether the deal closed won — accepts `yes`, `true`, `1`, `y`, `TRUE`, `FALSE`, `Won`, `Closed Won` (case-insensitive). The dashboard also infers this from stage name and close date. |

### Supported date formats

The dashboard accepts all of the following:

- `YYYY-MM-DD` (e.g. `2024-03-15`)
- `MM/DD/YYYY` (e.g. `03/15/2024`)
- `M/D/YYYY` with no leading zeros (e.g. `3/5/2024`)
- `M/D/YY` with two-digit year (e.g. `3/5/24`)
- `DD-Mon-YYYY` (e.g. `5-Mar-2024`)
- ISO 8601 with timestamp (e.g. `2024-03-05T10:00:00`) — the time component is ignored

### Channel naming tips

- Channel names are case-sensitive and must be consistent. "Paid Search" and "paid search" are treated as different channels.
- Common channel names: Organic Search, Paid Search, Paid Social, Social Media, Email, Webinar, Content Syndication, Display Ads, ABM, BDR Sourced, AE Sourced, Live Event, Inbound Email/Phone Inquiry
- Channel names with special characters (parentheses, slashes, etc.) are fully supported on all tabs including Cost & ROI

### What if I don't have all the columns?

That's fine. Mark any column as "not in my data" during the mapping step. The dashboard works with whatever you have — tabs that depend on missing data will simply be empty.

The one hard requirement is **First Touch Channel** and **Lead Created Date** — the dashboard will prompt you if these aren't mapped before loading.

---

## Attribution models explained

| Model | How credit is assigned | Best for |
|---|---|---|
| **W-Shaped** | 30% First Touch · 30% Pipeline Touch · 30% Last Touch · 10% split across middle touches. For leads with no middle touches, the 10% is redistributed proportionally across the key touches that exist. | Balanced view of the full buyer journey |
| **U-Shaped** | 40% First Touch · 20% split across middle touches · 40% Last Touch. For leads with no middle touches, the 20% is redistributed equally between First and Last Touch. | Emphasizing awareness and close, less weight on pipeline creation |
| **Linear** | Equal credit split across every touchpoint | Valuing nurture and mid-funnel engagement |
| **First Touch** | 100% to the channel that generated the lead | Understanding reach and awareness |
| **Last Touch** | 100% to the channel present at close | Understanding what's winning deals |

---

## Cost & ROI tab

Enter your actual monthly spend per channel to unlock ROI, payback period, cost-per-lead, cost-per-MQL, cost-per-opp, and pipeline coverage metrics.

**For accurate ROI, include all costs — not just ad spend:**
- Program costs (events, sponsorships, content production)
- Tool and platform fees (marketing automation, ABM software, data providers, SEO tools)
- Labor costs (headcount time allocated to each channel)
- Agency and vendor fees

Organic channels like Organic Search and Social Media aren't free — include the cost of the people and tools that power them.

Charts on this tab populate once you've entered spend for at least one channel. Channels with spend but $0 ARR won are flagged as **Negative** ROI in red.

---

## Tips for getting the most out of the dashboard

- **Start with the Channel Scorecard** (first tab) to get the full picture before drilling in
- **Compare attribution models** — a channel that looks weak in First Touch may be a strong closer, or a strong nurture channel invisible in single-touch views
- **Middle Touches tab** reveals channels that are invisible in first/last touch models but appear heavily in the nurture journey
- **Funnel Velocity tab** only shows channels with actual closed deals in the lead-to-close and SQL-to-close charts — channels with no won deals are excluded to avoid misleading zeros
- **Filter by industry or company size** to see if attribution patterns differ across ICP segments
- **Pipeline Value** on the KPI bar is calculated from your actual average deal size — if you have no closed-won deals in the dataset, pipeline value will not display

---

## Technical notes

- Single self-contained HTML file — no backend, no dependencies to install, no data leaves your browser
- Uses [Chart.js 4.5.1](https://www.chartjs.org/) for charts and [PapaParse 5.4.1](https://www.papaparse.com/) for CSV parsing, both loaded from CDN (requires internet connection on first load)
- Tested in Chrome, Safari, Firefox, and Edge — does not support Internet Explorer
- Works with CSVs exported from Salesforce, HubSpot, Marketo, and most CRM/MAP platforms

---

## Sample data

The included sample data (`Multitouch_Attribution_Combined.csv`) contains 2,000 fictional leads across 13 channels, spanning June 2023 – March 2025. It is entirely made up — no real names, companies, or contact information. It is designed to tell a realistic story: Organic Search and Live Event source the highest-quality pipeline, BDR Sourced wins the most deals, ABM brings the largest average deal size, and high-volume channels like Paid Search and Paid Social have lower conversion rates.

---

## Known limitations

- The dashboard assumes one row per lead. If your CRM exports one row per activity or touchpoint, you will need to reshape your data before uploading.
- The Cost & ROI tab uses monthly spend × number of months in your dataset to calculate total spend. If your dataset only covers 2 months but you want to model annual ROI, adjust your monthly spend input accordingly.
