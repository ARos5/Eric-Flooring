# The LVP Warehouse Newsletter — Implementation Plan

How the newsletter goes from "mockup" to "sends itself." Built around **Mailchimp** (see platform
recommendation at the end). Companion docs: `data-sources.md` (where the market numbers come from)
and `monday-meeting-agenda.md` (what to do/collect Monday).

---

## 1. Audience pipeline — QuickBooks → Mailchimp

Goal: get Eric's ~100 customers (name, email, phone, and ideally purchase history) into Mailchimp,
cleanly. Two paths depending on which QuickBooks he runs:

### Path A — Native sync (best; QuickBooks **Online**)
Mailchimp is owned by Intuit, so there's a first-party connection.
1. In Mailchimp → **Integrations** → connect **QuickBooks Online**.
2. It syncs customers into a Mailchimp **Audience**, and can carry **purchase/transaction data**
   (great for segmenting by spend/recency — see §2).
3. New/edited QuickBooks customers keep syncing automatically — no re-exporting.

### Path B — CSV export/import (QuickBooks **Desktop**, or to start fast)
1. QuickBooks → **Customers/Reports → Customer Contact List** → **Export to CSV/Excel**.
2. Clean the file first ("good in, good out"): dedupe, drop blank/invalid emails, split first/last
   name, normalize phone, add a **city/ZIP** column for local relevance.
3. Mailchimp → **Audience → Import contacts → CSV** → map columns to fields/tags.

> **AI assist (now):** hand the raw export to Claude/ChatGPT to dedupe, fix formatting, and
> **propose tags** (Investor vs. Contractor vs. Homeowner) from purchase history and any QuickBooks
> notes — then review before import.

**Fields to carry:** First name, Last name, Email, Phone, City, ZIP, Tags, Last purchase date,
Lifetime spend, Designs purchased.

**Compliance:** Mailchimp requires a real physical address in the footer and a working unsubscribe
(CAN-SPAM) — both are already in the mockup. Only email people who've bought from or inquired with
Eric (legitimate existing relationship).

---

## 2. Segmentation

One Mailchimp **Audience**, organized with **Tags** + **Segments** (don't make multiple audiences —
it splits the free quota and duplicates contacts).

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
flips, 3–6 month turns, mostly cosmetic). So the newsletter's job is to be in the inbox *before* that
flooring decision.

- **Active Buyers — quarterly (4×/yr):** the full issue (market pulse + new designs + deal). Enough
  to stay top-of-mind without fatigue.
- **Investor Prospects — every 4–6 weeks:** a lighter format (one headline stat + the flip special +
  one new design). Higher frequency catches them in that 1-month post-purchase window.
- **Contractors — quarterly + occasional deal blast.**
- **Send timing:** mid-week (Tue–Thu), late morning. Tune from open/click data after a few sends.

> Start here; let engagement data adjust it. If prospects open every send, hold the pace; if opens
> drop, ease off.

---

## 4. Automation — how it runs itself

1. **Template once:** rebuild this mockup as a saved **Mailchimp template** (drag-and-drop). Logo,
   colors, sections, footer all locked in.
   - **Image production note (important):** email clients don't reliably render **SVG** or
     CSS-drawn swatches. Before a real send, export Eric's logo as a **hosted PNG** and upload
     **real design photos** (JPG/PNG) — Mailchimp hosts them for you. The mockup's inline SVG logo
     and CSS wood swatches are **preview-only** stand-ins, not what goes out in the actual email.
2. **Quarterly issue → scheduled Regular Campaign** to *Active Buyers* (and Contractors). Build it,
   schedule the date, done.
3. **Prospect cadence → a Customer Journey / recurring automation** so the lighter issue goes out on
   its own every 4–6 weeks.
4. **Refreshing the data each issue:** the only real recurring work. Pull the latest numbers from the
   sources in `data-sources.md` (NEFAR mid-month, Freddie Mac weekly) and update the six stats + the
   takeaway. ~15 minutes with the AI assist below.

**Where AI fits**
- **Now:** a saved prompt that (a) fetches the latest NEFAR + Freddie Mac figures, (b) drafts the
  "what this means for flippers" paragraph, (c) writes 3 subject-line options, (d) cleans any new
  contacts. Eric/Alex review and hit send.
- **Later (the agent Eric asked about):** a scheduled agent (Mailchimp API + Zapier) that assembles
  the issue from live data and queues it for one-click approval — and the separate inventory/lead
  agents he floated.

---

## 5. Platform recommendation — Mailchimp vs. Beehiiv

**Recommendation: start on Mailchimp.**

| | **Mailchimp** ✅ start here | **Beehiiv** |
|---|---|---|
| QuickBooks sync | **Yes** (Intuit-owned, native) | No |
| Free tier | 500 contacts, ~1,000 sends/mo (fits ~100 easily) | Free up to 2,500 subs |
| Segmentation/automation | Strong, mature | Good, simpler |
| Sponsorships | Manual (just works) | **Built-in ad network + referral growth** |
| Learning curve | Familiar, more features | Cleaner/simpler editor |

**Why Mailchimp now:** the QuickBooks tie-in removes the biggest friction (getting contacts in and
keeping them current), the free tier covers Eric's list, and segmentation/automation are more than
enough. **Revisit Beehiiv** later *if* sponsor slots and referral-driven growth become the main
focus — its built-in ad/referral tooling is genuinely nicer for that. Decide together Monday.

---

## 6. Sequence to go live (with Eric, Monday+)

1. Create Mailchimp account; set business name/address/from-email.
2. Connect QuickBooks (Path A) **or** import the cleaned CSV (Path B).
3. Apply tags; build the three segments.
4. Rebuild the mockup as a Mailchimp template (drop in real logo + photos).
5. Draft issue #1 with current data; send a test to Eric.
6. Schedule the first quarterly send; set up the prospect automation.
7. Set a recurring 15-min "refresh the data + send" reminder.
