# System: Inventory Management

*Last updated: May 2026 | Owner: Kris | Review cadence: Weekly scan, Monthly full review*

---

## 1. Purpose

Ensure Phlippens always has the right amount of finished product on hand — enough to fill reorders quickly and run tasting events without scrambling, but not so much that cash is tied up in jars sitting in storage. At this stage, inventory management is a simple discipline: know what you have, know what you need, and never let a good account go unserviced because product wasn't ready.

---

## 2. Scope

**In scope:**
- Finished goods inventory (jarred, labelled, ready to ship or deliver)
- Sampling and tasting stock (set-aside product reserved for tastings and events)
- Raw ingredient stock (garlic, onions, fruitwood, jars, lids, labels)
- Packaging materials (boxes, inserts, story cards)

**Out of scope:**
- Production scheduling (goes in `system-production-copacker.md`)
- Retail account sell-through tracking (goes in `system-retail-velocity-engine.md`)
- DTC order fulfillment routing (goes in `system-dtc-funnel.md`)

---

## 3. Inputs

- **Finished goods count** — physical count of jars on hand by SKU (current SKU: hand-smoked garlic & onion condiment; note any future SKUs when introduced)
- **Pending orders** — retail reorders confirmed or anticipated in the next 14 days
- **Upcoming tasting events** — from the tasting schedule in `system-retail-velocity-engine.md`
- **DTC order velocity** — average weekly DTC orders from Shopify
- **Production run output** — units produced per run from `system-production-copacker.md`
- **Ingredient levels** — garlic, onions, fruitwood, jars, lids, labels — are any inputs running low?

---

## 4. Outputs

- **Weekly inventory snapshot** — current units on hand, units reserved for tastings, units available for orders
- **Reorder flag** — alert when finished goods fall below the reorder threshold (defined in Section 6)
- **Production trigger** — signal to `system-production-copacker.md` that a new production run is needed
- **Ingredient purchase list** — what inputs need to be sourced before the next production run
- **Monthly inventory report** — ending stock by SKU, units shipped by channel, shrinkage or waste notes

---

## 5. Workflow

**Step 1 — Weekly count (Monday, 15 min)**
Physical count of finished goods on hand. Update the inventory log:
- Units available for orders
- Units reserved for this week's tasting events
- Units reserved as DTC buffer stock

**Step 2 — Check against demand (Monday, 10 min)**
- Pull pending retail reorders from the account log
- Pull DTC order average from Shopify
- Add tasting reserve from this week's tasting schedule
- Total demand vs. units on hand = surplus or deficit

**Step 3 — Flag low stock (as triggered)**
If finished goods fall below the reorder threshold (see Section 6), immediately flag to production system and begin ingredient sourcing. Do not wait until stock is depleted.

**Step 4 — Ingredient check (pre-production)**
Before every production run, verify ingredient levels. Any input running below a 2-run buffer gets sourced immediately. Supplier lead times documented for each key input.

**Step 5 — Monthly reconciliation (first week of each month, 20 min)**
- Count finished goods on hand vs. expected (opening stock + produced - shipped)
- Note any discrepancy (waste, breakage, sampling over-allocation)
- Update the monthly inventory report in the finance/ops sheet
- Flag any ingredient suppliers who underdelivered on lead time

---

## 6. Cadence

**Weekly:**
- Monday inventory count and demand check (15–25 min)
- Reorder flag reviewed — is a production run needed in the next 2 weeks?

**Monthly:**
- Full inventory reconciliation
- Ingredient supplier check — any upcoming lead time issues?
- Report to `system-ar-cashflow.md` — cost of goods in the month

**Quarterly:**
- Inventory strategy review — is the reorder threshold right for current demand?
- Seasonal demand planning — summer grilling (May–August) and holiday gifting (Nov–Dec) require pre-building stock
- Packaging materials review — story cards, labels, boxes: reprint schedule

### Reorder thresholds (starting point — adjust as demand data builds)

| Stock type | Reorder trigger | Target buffer |
|---|---|---|
| Finished goods (retail) | Below 4 weeks of average reorder demand | 6–8 weeks on hand |
| Finished goods (DTC) | Below 3 weeks of average DTC order velocity | 5–6 weeks on hand |
| Tasting / sampling stock | Below 50 sample units | Top up to 100 before next tasting |
| Story cards | Below 50 units | Reprint to 200+ |
| Labels | Below 1 production run equivalent | Order 2-run equivalent |

---

## 7. Tools & Data Sources

| Tool | Purpose |
|---|---|
| Inventory log (Google Sheet or Notion) | Running count of finished goods by SKU, ingredient levels, weekly snapshot |
| Shopify | DTC order velocity — pulls average weekly orders for demand planning |
| Account reorder log | Retail demand signal — pending and anticipated reorders |
| Supplier contacts | Lead time reference — documented for each key ingredient |

---

## 8. Interfaces With Other Systems

**Reads from:**
- `system-production-copacker.md` — production run output, production schedule
- `system-retail-velocity-engine.md` — tasting schedule and anticipated account demand
- `system-dtc-funnel.md` — DTC order velocity

**Writes to:**
- `system-production-copacker.md` — production trigger when stock falls below threshold
- `system-ar-cashflow.md` — COGS for the month, inventory asset value
- `02-company-goals-okrs.md` — zero stockout KR tracking

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Weeks of stock on hand | Finished goods / average weekly demand (all channels) | Weekly | 6–8 weeks |
| Stockouts at active accounts | Times an account couldn't be fulfilled when ordered | Monthly | Zero |
| Tasting fill rate | Tastings supplied with product vs. tastings scheduled | Monthly | 100% |
| Ingredient lead time compliance | Suppliers delivering within stated lead time | Monthly | All key inputs on time |
| Shrinkage / waste rate | Units lost to breakage, over-sampling, or expiry | Monthly | Below 2% of production run |

---

## 10. AI Opportunities

**Demand forecasting assistant:**
Paste the last 3 months of reorder data and the upcoming tasting/event schedule. Ask Claude to estimate demand for the next 6 weeks by channel and flag if current stock is sufficient. Useful before seasonal peaks.

**Ingredient purchase list generator:**
Give Claude the production run size and the current ingredient log. Ask it to generate a shopping list with quantities, supplier names, and lead time notes. Prevents the "I forgot to order lids" problem.

**Monthly inventory report writer:**
Paste the weekly count snapshots from the month. Ask Claude to format them into a clean monthly inventory report with a brief commentary on any anomalies. 10 minutes of data becomes a structured document.
