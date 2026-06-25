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

## The hard part: off-market / wholesale ("off-MLS") activity

Eric specifically wants the investor/wholesale angle. Honest assessment: **there is no clean, free,
public feed of off-MLS deals.** Options, cheapest → most real:

1. **Proxy metrics from public/affordable data (recommended for v1).** You can't see assignment
   deals directly, but you can track signals investors care about:
   - **Cash-sale share** and **absentee-owner purchases** (ATTOM / county records).
   - **Foreclosure & auction volume** (ATTOM / RealtyTrac).
   - **County property-appraiser & clerk records** for Duval, Clay, St. Johns — public but messy;
     good for cash/quitclaim/assignment patterns with some cleanup.
   Label these as "investor activity indicators," not literal wholesale counts.
2. **Investor data tools (paid).** PropStream (~$99/mo), BatchLeads, InvestorLift, DealMachine —
   distressed/absentee/cash lists and comps. Most direct path to real off-market numbers; costs money.
   Decide with Eric whether the section is worth a subscription.
3. **Partner data.** Eric talks to local wholesalers already — a wholesaler partner could share
   aggregate stats (deal count, price bands) in exchange for a sponsor mention. Cheap and very local.

**v1 decision:** the mockup's off-market block is clearly marked **"Preview · data source TBD."**
Until a source above is chosen, keep it labeled as a sample. Recommended first step: proxy metrics
(option 1) + explore a wholesaler partnership (option 3); upgrade to a paid tool only if it pays off.

---

## Refresh checklist (per issue)
1. Pull the latest **NEFAR** monthly report → update the 5 housing stats + their YoY/MoM deltas.
2. Grab this week's **Freddie Mac** 30-yr rate.
3. Update the "what this means for flippers" line to match the new numbers.
4. Update the off-market block once a real source is live (until then, leave the sample tag).
5. Re-state the reporting month on the source line.
