# System: Retail Velocity Engine

*Last updated: May 2026 | Owner: Kris | Review cadence: Monthly tiering, Quarterly playbook refresh*

---

## 1. Purpose

Create a simple, repeatable system to increase units per store per week in existing retail doors. Phlippens already has 50+ reordering accounts — the gap is not distribution, it's depth. This system turns that existing footprint into a compounding velocity asset by ensuring the right stores get the right support at the right time, consistently, without requiring Kris to hold everything in his head.

---

## 2. Scope

**In scope:**
- Existing independent retail doors in Waterloo Region
- In-store tastings and demos at active accounts
- Basic promos tied to seasons and key moments (summer grilling, holiday gifting)
- Shelf presence upgrades: counter placement, end caps, shelf talkers, story cards
- Foodservice accounts where the chef reorders (treated as velocity accounts, not a separate system)

**Out of scope:**
- National or regional chain grocery (different margin structure, different system)
- New product development (goes in the Operations system)
- Ecommerce-only promotions (goes in the DTC Funnel system)
- New account acquisition beyond natural fit referrals (Layer 2 work, not this system)

---

## 3. Inputs

- **Store list** with tier classification (A/B/C) and account details (owner name, last order date, placement quality, relationship notes)
- **Sales/reorder data** by account — at minimum, last order date and estimated order size; ideally, reorder frequency trend over time
- **Inventory on hand** — how much product is available for sampling and restocking in the next 4–6 weeks
- **Upcoming calendar events** — seasons (summer grilling, holiday), local food events, MWWT walks near retail accounts, golf tournament
- **Story card and POS inventory** — how many printed story cards, shelf talkers, and display materials are on hand
- **Brand content** — which content is live or coming that ties into product (recipe Reels, KIPR episodes) that accounts can reference

---

## 4. Outputs

- **Monthly store tiering and focus list** — which accounts get active support this month, which are on maintenance, which need a check-in call
- **Tasting and demo schedule** — confirmed dates, locations, and logistics for the next 4–6 weeks
- **Shelf-talker / POS deployment plan** — which accounts get what materials and when
- **Monthly velocity report** — units per store per week by tier, tasting impact, any account movement between tiers
- **Outreach log** — record of every account interaction (visit, call, delivery, tasting) so nothing falls through the cracks

---

## 5. Workflow

**Step 1 — Pull latest store data (monthly, ~20 min)**
Open the account reorder log. Update last order dates and any notes from the prior month's visits and deliveries. Flag any accounts that haven't reordered in 60+ days for a check-in.

**Step 2 — Tier stores (monthly, ~30 min)**
Score each account across two axes: current performance (reorder frequency, estimated volume) and potential (placement quality, owner engagement, foot traffic). Assign A/B/C tier:
- **A accounts** — high velocity, featured placement, engaged owner. These get monthly in-person visits and priority sampling support.
- **B accounts** — moderate velocity, standard shelf placement, responsive owner. These get quarterly tastings and a monthly check-in call or delivery touchpoint.
- **C accounts** — low reorder frequency, poor placement, or low owner engagement. These get a 60-day check-in and an honest assessment of whether the relationship is worth continuing.

**Step 3 — Decide support for next 4–6 weeks (monthly, ~30 min)**
Based on the tier list, the upcoming calendar, and available inventory, decide:
- Which A accounts get tastings this month?
- Which B accounts are ready to be upgraded (better placement ask)?
- Which C accounts need a conversation about whether the fit is still right?
- Any seasonal or event-driven promos to attach to specific accounts?

**Step 4 — Coordinate logistics (weekly, rolling)**
- Confirm tasting dates with account owners at least one week out
- Pull product for tasting batches (sample jars, serving materials)
- Print or pull story cards and any POS materials for the accounts being visited
- Add confirmed tastings to the shared calendar

**Step 5 — Run tastings and collect quick notes (as scheduled)**
- Tasting format: product on a real surface (not a folding table if avoidable), story card visible, restaurant anchor story ready to tell
- Notes captured same day: how many samples given, any standout reactions, new contacts made, QR code scans observed
- Any new email sign-ups captured and added to Klaviyo

**Step 6 — Review impact and adjust (monthly, ~20 min)**
- Did reorder velocity change in accounts that had tastings vs. those that didn't?
- Did any placements improve?
- Any accounts ready to move up a tier?
- What worked in the tasting format? What didn't?

---

## 6. Cadence

**Weekly:**
- Quick scan of orders received — any accounts running low? Any stockouts to prevent?
- Any deliveries this week? Add relationship touchpoints to all delivery runs.
- Tasting logistics confirmed for the coming week.

**Monthly:**
- Full store tiering review (Step 1–3 above)
- Tasting and support schedule set for next 4–6 weeks
- Velocity report generated and reviewed against KPIs
- Story card and POS inventory checked — reprint if below 50 units

**Quarterly:**
- Playbook review — is the tiering system working? Is the tasting format converting?
- Any accounts to graduate to the foodservice system?
- Any accounts to exit (not worth the cost of continued support)?
- Seasonal promo planning for the next quarter's key moments

---

## 7. Tools & Data Sources

| Tool | Purpose |
|---|---|
| Account reorder log | Source of truth for store list, tier, last order date, placement quality, contact name — lives in Notion or Google Sheet |
| Shared calendar (Google) | Tasting schedule, delivery runs, account visits |
| Klaviyo | Captures email sign-ups from tasting events |
| Instagram Insights | Which content accounts can point customers to (recipe Reels, KIPR episodes) |
| Story cards / shelf talkers | Physical POS — printed in batches of 200+, restocked monthly |

*Note: Until a formal CRM is in place, the account reorder log in Notion/Google Sheet IS the CRM. Keep it current — it's the only place Kris can hand off account knowledge to someone else.*

---

## 8. Interfaces With Other Systems

**Reads from:**
- `system-inventory-management.md` — available product for sampling and restocking
- `01-strategy-2026-roadmap.md` — which accounts and regions are in focus this quarter
- `system-content-engine.md` — which content is live that can be attached to account conversations

**Writes to:**
- `02-company-goals-okrs.md` (KPI table) — velocity KPIs, tasting counts, tier movement
- `system-ar-cashflow.md` — reorder events trigger AR entries
- `03-operating-cadence.md` — tasting schedule feeds the marketing calendar
- `system-ai-projects-index.md` — tiering and outreach drafting are live AI use cases

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Units per store per week (by tier) | Average units sold per active account per week, broken out by A/B/C | Monthly | A accounts: improving trend; B accounts: stable or improving |
| Tasting events run | Number of in-store tastings completed in the month | Monthly | Minimum 2/month during active campaign; 1/month at minimum |
| Velocity change post-tasting | Reorder volume in the 30 days after a tasting vs. 30 days before | Monthly | Positive delta in 70%+ of tasting events |
| Featured placement count | Accounts with counter, end cap, or signage placement | Monthly | 20+ by end of Q3 2026 |
| Account tier distribution | How many A/B/C accounts, and is the mix improving? | Quarterly | A tier growing, C tier shrinking |
| Days since last order (avg by tier) | Average reorder cycle length by tier | Monthly | A accounts reordering faster than B; C accounts flagged at 60 days |

---

## 10. AI Opportunities

**Monthly tiering agent:**
Paste the account reorder log into Claude. Ask: "Based on reorder frequency, days since last order, and placement quality, suggest a tiering for next month and identify the top 5 accounts to prioritize for tastings." Saves 30 minutes of manual sorting and surfaces patterns that are easy to miss when looking row by row.

**Tasting schedule generator:**
Give Claude the tier list, available dates, and inventory on hand. Ask it to propose a 4–6 week tasting schedule that prioritizes A accounts and high-potential B accounts, avoiding scheduling conflicts with MWWT walks and other events.

**Account outreach drafter:**
For check-in calls and tasting invitations, give Claude the account name, owner name, last interaction, and current tier. Ask it to draft a short, warm outreach message in Kris's voice. Takes 30 seconds instead of 10 minutes of staring at a blank message screen.

**Post-tasting summary:**
After a tasting, voice-note or type quick observations into Claude. Ask it to turn them into a structured tasting log entry (date, location, samples given, reactions, leads captured, next action). Keeps records consistent without Kris having to write up notes in a formal format.
