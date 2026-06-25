# Data Sources — Northeast Florida Market Pulse

Where every number in the newsletter comes from, how often to refresh it, and an honest take on the
hard part (off-market/wholesale). The goal is that any issue can be refreshed in ~15 minutes and
every figure is real and citable.

> **Rule:** never fabricate a number. Label each stat with the period it covers. If a source isn't
> available for an issue, drop the stat rather than guess.

---

## Primary sources (free, recurring)

| Source | What you get | Refresh | Link |
|---|---|---|---|
| **NEFAR** — Northeast FL Association of REALTORS®, monthly market reports | Median price, closed sales, pending sales, active inventory, % sold over list, months of supply — for the **6-county region** (Baker, Clay, Duval, Nassau, Putnam, St. Johns). **This is the anchor source.** | Monthly, ~mid-month | nefar.realtor/market-stats |
| **Freddie Mac PMMS** | National avg **30-yr & 15-yr fixed mortgage rate** | Weekly (Thu) | freddiemac.com/pmms |
| **Florida Realtors — Market Data** | State + metro (Jacksonville MSA) monthly stats; good cross-check | Monthly | floridarealtors.org/newsroom/market-data |
| **Redfin Data Center / Zillow Research** | Downloadable Jacksonville-metro time series: median sale price, days on market, inventory | Monthly | redfin.com/news/data-center · zillow.com/research/data |
| **FRED (MORTGAGE30US)** | Mortgage-rate history for charts/trends | Weekly | fred.stlouisfed.org/series/MORTGAGE30US |
| **Jax Daily Record / News4Jax** | Local color + quotes to contextualize the numbers | As published | jaxdailyrecord.com |

### Numbers used in the v1 mockup (for traceability)
- Median sale price **$410,000**, **+6.1% YoY** — NEFAR, **May 2026**.
- Closed sales **1,969**, **+2.9% MoM** — NEFAR, **May 2026**.
- Active inventory **7,109**, **−15.1% YoY** — NEFAR, **May 2026**.
- Median days on market **~50**, ~4-month supply — NEFAR / metro data, mid-2026.
- 30-yr fixed **~6.5%** — Freddie Mac PMMS, **June 2026**.
- Sold over list **14.1%** (vs. 11.3% a year ago) — NEFAR, **May 2026**.

*(Refresh all six from the same period each issue so the snapshot is internally consistent.)*

---

## Off-market / investor activity ("Off-Market Real Estate Trends")

**Solved.** There's no free feed of literal off-MLS *assignment* deals — but the **investor signals
that matter are publicly trackable on a repeatable cadence**, and Jacksonville is a national hotspot.
This is the approach (and the exact figures used in the v1 mockup):

| Metric | Figure used | Source · cadence |
|---|---|---|
| **All-cash share** | **39.3%** — Jacksonville tied #1 in the U.S. | Redfin (reported via WLRN, Feb 2026) · ~quarterly |
| **Investor / cash buyers** | **~28%** of transactions (vs. ~18–20% historically) | Redfin / local market analyses · quarterly |
| **Avg. flip gross margin** | **~27%** metro (Jacksonville) | **ATTOM Home Flipping Report** · quarterly |
| **Hot flip ZIPs (sub-$200k)** | 32210 (Westside) · 32218/32208 (Northside) · 32206 (Springfield) | local investor-market analyses + county records |
| **Foreclosure / auction volume** | live Duval auction calendar | **Duval County Clerk** foreclosure auctions (RealAuction) · ongoing |

**How to refresh each issue:** pull the latest **Redfin** all-cash/investor share, the **ATTOM**
Home Flipping Report (metro flip rate + ROI), and the **Duval County Clerk** auction calendar; refresh
hot ZIPs/price bands from local investor analyses + the county property appraiser. All free.

**If Eric wants deeper, real-time data later:** a paid investor tool (**PropStream** ~$99/mo) for
distressed/absentee/cash lists, or **aggregate stats from a wholesaler partner** (cheap, hyper-local,
and a natural sponsor tie-in).

---

## Refresh checklist (per issue)
1. Pull the latest **NEFAR** monthly report → update the 5 housing stats + their YoY/MoM deltas.
2. Grab this week's **Freddie Mac** 30-yr rate.
3. Update the "what this means for flippers" line to match the new numbers.
4. Refresh the off-market figures: **Redfin** all-cash/investor share (quarterly), **ATTOM** flip ROI
   (quarterly), **Duval County Clerk** auction calendar (live).
5. Re-state the reporting month on the source line.
