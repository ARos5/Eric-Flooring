# The LVP Warehouse — Newsletter — Spec

**Status:** Draft
**Date:** 2026-06-25
**Author:** Alex R. (via /spec interview, from the 2026-06-25 call with Eric Borrelli)

> Note on location: the /spec skill normally writes to `~/Documents/Claude/Projects/specs/`.
> Because this work lives in the `Eric-Flooring` repo and is built/reviewed in a remote
> environment, the spec is versioned here at `specs/newsletter.md` so `/build` and
> `/spec-review` can find it alongside the project.

## Objective

Build a recurring, **automated email newsletter** for **The LVP Warehouse — Jacksonville**
(Eric Borrelli's luxury-vinyl-plank flooring business) that keeps the company top-of-mind with
**Northeast Florida real estate investors, flippers, repeat buyers, and general contractors**.
Each issue pairs **Northeast Florida real estate market data** (the hook that this audience
actually cares about) with **flooring design showcases and promotions**, so that when an
investor closes a flip, The LVP Warehouse is who they call for flooring.

Success looks like: a polished, on-brand newsletter that Eric is proud to send; an audience
imported and segmented from his QuickBooks customers; and an automated send cadence that runs
with minimal ongoing effort — eventually self-funding via local sponsor slots.

For the **immediate milestone (Alex's Monday 6/29 2pm meeting with Eric)** the deliverable is a
**look-and-feel mockup + an implementation plan**, not a live send. Live setup (importing Eric's
real contacts, connecting QuickBooks) happens with Eric present, since his data isn't available
beforehand.

## Requirements

### A. Newsletter mockup (the v1 deliverable)

1. A single, **openable HTML email mockup** titled **"The LVP Warehouse — Jacksonville"** that
   renders correctly in a desktop browser and on a phone (so Alex can show Eric live).
2. Branding matches Eric's existing **black-and-white "LVP Warehouse" logo** (house/gable
   outline, bold "LVP", "WAREHOUSE", plank-floor motif), **plus a bolder accent color** used for
   data highlights and calls-to-action.
3. The mockup must contain these content blocks, populated with **realistic sample data** (clearly
   labeled as sample where it's a placeholder):
   - **Header** — logo + "Jacksonville" + issue label (e.g., "Q3 2026 · Northeast Florida").
   - **Short intro/note** voiced as Eric.
   - **Northeast Florida Market Pulse** — a scannable data section: median sale price + YoY,
     closed sales, active inventory + YoY, days on market, 30-year mortgage rate, % sold over
     list. Each stat sourced from real recent figures (see `docs/data-sources.md`).
   - **A plain-English "what this means for flippers" takeaway** that ties the market data back
     to flooring demand.
   - **Off-market / wholesale watch** — a short investor-focused callout (the off-MLS angle Eric
     asked for), with sourcing caveats noted in the plan.
   - **Featured Floors** — 2–3 showcased LVP designs (placeholder swatches/photos + names),
     structured so Eric drops in real product photos.
   - **Promotion** — the **"Investor Flip Special — LVP from $1.49/sq ft"** (the separate cheaper
     flip line), marketed **under The LVP Warehouse brand only — never the CASE brand**. Also
     surface the repeat-buyer price ($1.69/sq ft).
   - **Sponsor slot** — a clearly-marked placeholder showing the future "sponsored by a local
     general contractor" monetization.
   - **Clear CTA** — contact / reserve-a-pallet / book-a-sample-visit.
   - **Footer** — business contact (LVPJacksonville@gmail.com), physical-address placeholder,
     social ("Case Floors"), and a working-style **unsubscribe link** (CAN-SPAM requirement).
4. The mockup is built so brand assets (real logo PNG, brand colors, real design photos, address)
   can be **swapped in without restructuring**.

### B. Implementation plan (written, for the Monday meeting)

5. **Audience pipeline:** document how to get contacts from **QuickBooks → the chosen platform
   (Beehiiv)** (export/import path and, where possible, an automated/assisted path), including the
   fields to carry (name, email, phone, purchase history if available).
6. **Segmentation scheme:** define concrete segments — at minimum **"Active/definite buyers"** vs.
   **"Prospects / not buying now,"** with **real estate investors/flippers** called out — and the
   data signals used to assign people to each.
7. **Cadence plan:** a recommended send cadence per segment (quarterly for committed buyers, more
   frequent for prospects), with the reasoning, designed around the ~**1-month lag** between an
   investor buying a house and buying flooring.
8. **Automation plan:** how issues get assembled and sent on a schedule with minimal effort
   (Beehiiv scheduled posts/automations; how the market data gets refreshed each issue),
   including where AI assists.
9. **Data-sourcing doc:** list the specific, accessible sources for the Northeast Florida market
   numbers (and an honest assessment of how to get the off-market/wholesale angle), so each issue
   can be refreshed.
10. **Platform recommendation:** target **Beehiiv** (the chosen platform), and document **Mailchimp**
    as the alternative — reserved for Alex's other business unless Eric opens his own account.

### C. Meeting prep

11. A concise **Monday-meeting agenda/checklist** Alex can run from: what to show, what to collect
    from Eric (logo file, brand colors, design photos, QuickBooks access, address/hours), and the
    decisions to lock.

### Nice-to-haves (out of scope for v1)

- A live, configured Beehiiv account with Eric's real contacts imported and a scheduled send.
- An automated agent that finds new leads or tracks inventory (Eric floated both).
- A real sold sponsorship.
- Pulling genuine off-MLS/wholesale data feeds (vs. a documented approach + caveat).
- A BIMI verified-logo setup (the "neon logo in Gmail" Alex has).

## Constraints

- **Platform / environment:** Email newsletter. Mockup is a self-contained HTML file viewable in a
  browser/phone. Final sends via **Beehiiv** (Mailchimp reserved for Alex's other business).
- **Tech stack:** Email-safe HTML/CSS for the mockup. No build tooling required to open it. Use
  inline SVG for the logo in the mockup (note: convert to a hosted PNG for real sends, since some
  clients strip SVG).
- **Brand rules (non-negotiable):**
  - The **flip/discount line ($1.49/sq ft) must be marketed only under "The LVP Warehouse," never
    the CASE brand** — CASE is unaware Eric runs this side line.
  - Visual identity follows the existing black-and-white LVP Warehouse logo + one bolder accent.
- **Data integrity:** market figures must come from real, citable sources and be labeled with the
  period they cover; placeholders must be visibly marked as samples.
- **Audience source:** Eric's QuickBooks customer list (~100 contacts to start; name, email, phone).
- **Compliance:** marketing email must include a physical address + unsubscribe (CAN-SPAM).
- **Timeline:** mockup + plan ready before **Mon, June 29, 2:00 PM**.
- **Explicitly out of scope for now:** live sending, real contact import, lead/inventory agents,
  real off-market data feeds, sold sponsorships.

## Edge Cases & Failure Modes

- **Eric's real assets not available yet (logo file, colors, photos, address):** mockup uses a
  faithful recreation + clearly-labeled placeholders, structured for easy swap. Expected behavior:
  nothing breaks when real assets replace placeholders.
- **Off-market/wholesale data not reliably/freely available:** don't fabricate it. The data doc
  states what's obtainable vs. not, and the section uses a clearly-sample callout until a real
  source is confirmed.
- **Market data goes stale between issues:** each stat is labeled with its reporting period and
  the data doc lists where to refresh it, so a future issue isn't silently showing old numbers.
- **SVG/logo or images don't render in a real email client:** documented that logo → hosted PNG and
  design photos → hosted images are required before a real send; mockup remains the visual target.
- **Contact list has dupes/missing emails on QuickBooks export:** plan notes a dedupe/clean step
  before import ("good in, good out").
- **CASE brand exposure risk:** review step confirms the discount line nowhere references CASE.

## Definition of Done

- [ ] An HTML mockup titled "The LVP Warehouse — Jacksonville" opens cleanly in a browser and on a
      phone, on-brand (B&W logo + bolder accent).
- [ ] Mockup includes all blocks in Requirement 3, with realistic, sourced sample data and clearly
      marked placeholders.
- [ ] The $1.49/sq ft flip special appears under The LVP Warehouse brand with **no** CASE reference.
- [ ] Footer has contact info, address placeholder, and an unsubscribe link.
- [ ] `docs/implementation-plan.md` covers the QuickBooks→Beehiiv pipeline, segmentation, cadence,
      and automation (Requirements 5–8, 10).
- [ ] `docs/data-sources.md` lists real, citable NE-Florida data sources + the off-market caveat
      (Requirement 9).
- [ ] `docs/monday-meeting-agenda.md` gives Alex a runnable agenda + a list of what to collect from
      Eric (Requirement 11).
- [ ] All artifacts committed and pushed to branch `claude/sleepy-rubin-m0u2w5` in `Eric-Flooring`.

### Acceptance scenario

Alex opens the mockup on his phone at the Monday meeting. Eric sees a clean "LVP Warehouse"-branded
newsletter leading with real Northeast Florida market numbers, his flooring designs, the $1.49
investor special, and a sponsor slot. Alex then walks Eric through the plan doc — "we pull your
QuickBooks contacts into Beehiiv, split them into active buyers vs. investor prospects, and it
sends itself quarterly (more often to prospects)." Eric hands over his logo file, brand colors,
some design photos, and QuickBooks access, and they agree on cadence — everything needed to go live.

## Open Questions

- Platform: **Beehiiv** chosen (Mailchimp reserved for Alex's other business unless Eric opens his own).
- Can off-MLS / wholesale activity be sourced reliably and affordably for the investor section?
- Exact send cadence per segment (starting recommendation provided; tune from engagement data).
- Eric's real brand colors, final business name treatment, physical address, and hours.
- Whether to pursue the BIMI verified-logo setup so the "LVP Warehouse" mark shows in Gmail.
