# The LVP Warehouse Newsletter — Implementation Plan

How the newsletter goes from "mockup" to "sends itself." Built around **Beehiiv** (see the platform
decision in §5). Companion docs: `data-sources.md` (where the market numbers come from) and
`monday-meeting-agenda.md` (what to do/collect Monday).

> **Platform note:** We're using **Beehiiv** for The LVP Warehouse. Alex's **Mailchimp stays
> reserved for his other business.** If Eric later wants Mailchimp specifically (e.g., for its
> native QuickBooks sync), he'd create his **own** Mailchimp account — but the plan below assumes
> Beehiiv.

---

## 1. Audience pipeline — QuickBooks → Beehiiv

Goal: get Eric's ~100 customers (name, email, phone, and any purchase history) into Beehiiv, cleanly.
Beehiiv has **no native QuickBooks integration**, so this is a CSV import (with an optional automated
path via Zapier).

### Step 1 — Export from QuickBooks
- QuickBooks → **Customers / Reports → Customer Contact List** → **Export to CSV/Excel**.

### Step 2 — Clean the file first ("good in, good out")
- Dedupe, drop blank/invalid emails, split first/last name, normalize phone, add a **city/ZIP**
  column for local relevance, and add a **tag** column (Investor / Contractor / Homeowner).
- **AI assist (now):** hand the raw export to Claude/ChatGPT to dedupe, fix formatting, and
  **propose tags** from purchase history and any QuickBooks notes — then review before import.

### Step 3 — Import into Beehiiv
- Beehiiv → **Audience → Subscribers → Import** → upload CSV → map columns to **custom fields** and
  **tags**. Beehiiv supports custom fields + tags at import, which is what powers the segments in §2.

### Optional — keep it synced automatically (Zapier)
- Because there's no native QuickBooks↔Beehiiv connector, use **Zapier**: trigger **"New Customer in
  QuickBooks" → action "Create/Update Subscriber in Beehiiv."** New customers flow in without
  re-exporting. (Zapier is already available in our toolset; we can wire this up later.)

**Fields to carry:** First name, Last name, Email, Phone, City, ZIP, Tag(s), Last purchase date,
Lifetime spend, Designs purchased.

**Compliance:** marketing email needs a real physical address in the footer + a working unsubscribe
(CAN-SPAM) — both are already in the mockup, and Beehiiv adds the unsubscribe automatically. Only
email people who've bought from or inquired with Eric.

---

## 2. Segmentation

In Beehiiv, organize the one audience with **tags** (who someone is) + **segments** (dynamic groups
you actually send to, based on tags / custom fields / engagement).

**Tags (who they are):** `Investor/Flipper` · `General Contractor` · `Homeowner/Retail` ·
`Prospect` (inquired, no purchase) · `Repeat/VIP`.

**Core segments (how often they hear from us):**

| Segment | Who's in it (signals) | Cadence |
|---|---|---|
| **Active Buyers** | Purchased in last ~12 mo, or repeat buyers (`Repeat/VIP`) | **Quarterly** |
| **Investor Prospects** | `Investor/Flipper` + inquired-but-not-bought, or last buy >12 mo ago; multiple property addresses; pallet-size orders | **Every 4–6 weeks** |
| **Contractors / GCs** | `General Contractor` | Quarterly + ad-hoc deal blasts; also sponsor prospects |

**Signals used to assign people:** purchase recency/frequency, order volume (pallet buyers ≈
investors), multiple shipping addresses, QuickBooks customer type/notes, and how they came in.

---

## 3. Cadence — and *why*

The key insight from the call: **investors buy a house, then buy flooring ~a month later** (hard-money
flips, 3–6 month turns, mostly cosmetic). The newsletter's job is to be in the inbox *before* that
flooring decision.

- **Active Buyers — quarterly (4×/yr):** the full issue (market pulse + new designs + deal).
- **Investor Prospects — every 4–6 weeks:** a lighter format (one headline stat + the flip special +
  one new design). Higher frequency catches them in that 1-month post-purchase window.
- **Contractors — quarterly + occasional deal blast.**
- **Send timing:** mid-week (Tue–Thu), late morning. Tune from open/click data after a few sends.

> Start here; let engagement data adjust it.

---

## 4. Automation — how it runs itself

1. **Template once:** rebuild this mockup as a saved **Beehiiv post/template** (drag-and-drop
   editor). Logo, colors, sections, footer locked in.
   - **Image production note (important):** email clients don't reliably render **SVG** or
     CSS-drawn swatches. Before a real send, export Eric's logo as a **hosted PNG** and upload
     **real design photos** (JPG/PNG) into Beehiiv — it hosts them for you. The mockup's inline SVG
     logo and CSS wood swatches are **preview-only** stand-ins, not what goes out in the real email.
2. **Quarterly issue → scheduled post** to the *Active Buyers* segment (and Contractors). Build it,
   schedule the date, done.
3. **Prospect cadence → a Beehiiv Automation** so the lighter issue goes out every 4–6 weeks.
   *(Heads-up: automations/advanced segmentation may sit on a paid Beehiiv tier — confirm current
   plan limits; the free tier easily covers Eric's ~100-subscriber list for sending.)*
4. **Refreshing the data each issue:** the only real recurring work. Pull the latest numbers from
   `data-sources.md` (NEFAR mid-month, Freddie Mac weekly) and update the six stats + the takeaway.
   ~15 minutes with the AI assist below.

**Where AI fits**
- **Now:** a saved prompt that (a) fetches the latest NEFAR + Freddie Mac figures, (b) drafts the
  "what this means for flippers" paragraph, (c) writes 3 subject-line options, (d) cleans new
  contacts. Eric/Alex review and hit send.
- **Later (the agent Eric asked about):** a scheduled agent (Beehiiv API + Zapier) that assembles
  the issue from live data and queues it for one-click approval — plus the inventory/lead agents he
  floated.

---

## 5. Platform decision — Beehiiv (chosen), Mailchimp reserved

**Decision: build on Beehiiv.** Mailchimp is reserved for Alex's other business and won't host this.

| | **Beehiiv** ✅ chosen | **Mailchimp** (only if Eric opens his own) |
|---|---|---|
| QuickBooks sync | No native sync → CSV import (or Zapier) | Native (Intuit-owned) — but needs Eric's *own* account |
| Free tier | Up to ~2,500 subscribers, unlimited sends (covers ~100 easily) | 500 contacts, ~1,000 sends/mo |
| Monetization | **Built-in ad network, Boosts, referral program** — strong fit for Eric's "sponsor slot" idea | Manual |
| Editor | Clean, newsletter-native | More features, steeper |
| Automations | Yes (may be paid tier) | Yes |

**Why Beehiiv works here:** it's newsletter-native, the free tier covers Eric's list with room to
grow, and its **built-in sponsorship/referral tooling** lines up with the local-GC sponsor slot Eric
wants to sell. The only tradeoff vs. Mailchimp — no native QuickBooks sync — we solve with a clean
CSV import now and an optional Zapier sync later.

---

## 6. Sequence to go live (with Eric, Monday+)

1. **Eric** creates the Beehiiv account (name, business address, from-email = LVPJacksonville@gmail.com).
2. Export QuickBooks customers → clean the CSV → import into Beehiiv.
3. Apply tags; build the three segments.
4. Rebuild the mockup as a Beehiiv post/template (drop in real logo PNG + design photos).
5. Draft issue #1 with current data; send a test to Eric.
6. Schedule the first quarterly send; set up the prospect automation (verify plan tier).
7. Set a recurring 15-min "refresh the data + send" reminder. Optionally wire QuickBooks→Beehiiv via Zapier.
