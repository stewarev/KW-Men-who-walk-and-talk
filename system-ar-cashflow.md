# System: AR & Cash Flow

*Last updated: May 2026 | Owner: Kris | Review cadence: Weekly cash scan, Monthly full review*

---

## 1. Purpose

Keep Phlippens solvent and informed. A small bootstrapped business can be profitable on paper and bankrupt in practice if receivables are slow and payables are front-loaded. This system ensures that money coming in (accounts receivable from retail, DTC revenue, foodservice) is tracked against money going out (production costs, ingredients, marketing spend, any fixed costs), and that Kris always knows the cash position with enough lead time to make good decisions — not reactive ones.

---

## 2. Scope

**In scope:**
- Accounts receivable: invoices to retail accounts and any foodservice accounts on net terms
- DTC revenue: Shopify payouts (typically net 2–3 business days)
- Production costs: COGS per run (ingredients, packaging, labour estimate)
- Variable operating costs: sampling product, story card printing, tasting event costs, shipping
- Cash position: what's in the account, what's expected in, what's expected out over the next 30–60 days

**Out of scope:**
- Detailed tax preparation (handled by an accountant annually)
- Payroll (not applicable until a hire is made)
- Capital structure and investor relations (covered in `01-strategy-2026-roadmap.md` BDC note)

---

## 3. Inputs

- **Retail invoices** — invoice number, account name, amount, invoice date, payment terms (net 30 is standard for independent retail; confirm with each account), due date
- **DTC revenue** — Shopify payout schedule (typically 2–3 business days after sale)
- **Foodservice invoices** — as applicable; same tracking as retail
- **Production run costs** — ingredient costs + packaging costs + any co-packer fees per run (`system-production-copacker.md`)
- **Variable marketing spend** — story card printing, tasting event costs, any paid sampling product, shipping costs
- **Bank account balance** — actual cash on hand (checked weekly)
- **Upcoming large outflows** — any planned large purchases (bulk ingredient order, equipment, large print run) that need to be timed against incoming cash

---

## 4. Outputs

- **AR aging report** — all outstanding retail invoices by age (current, 30 days, 60 days, 90+ days)
- **Monthly cash flow summary** — cash in by channel vs. cash out by category, net position
- **30/60-day cash forecast** — expected inflows and outflows, projected ending cash balance
- **Overdue invoice flag** — any invoice past due date flagged immediately for follow-up
- **Channel margin report** — gross margin by channel (retail, DTC, foodservice) for `02-company-goals-okrs.md`

---

## 5. Workflow

**Step 1 — Invoice on delivery (same day as every retail or foodservice delivery)**
- Create invoice immediately. Don't batch them — invoicing delays extend payment delays.
- Invoice format: invoice number, date, account name, product quantity and SKU, unit price, total, payment terms (net 30 default), payment instructions (e-transfer, cheque, or online portal if set up)
- Send invoice by email on delivery day. Attach a PDF.

**Step 2 — Weekly cash scan (Monday, 15 min)**
- Check bank account balance
- Review AR aging: any invoices now overdue?
- Note any large outflows this week (production run, ingredient purchase)
- Quick gut check: is cash comfortable, tight, or a concern?

**Step 3 — Overdue invoice follow-up (as triggered)**
- At 5 days past due: send a polite reminder by email or text. Most small retailers pay late because they forgot, not because they can't.
- At 15 days past due: call the owner directly. Frame it as a check-in on the account, not a collections call.
- At 30 days past due: escalate to a direct payment request. Note in the account log — this affects tier status.
- At 60 days past due: suspend new shipments until payment is received.

**Step 4 — Monthly cash flow review (first week of each month, 30 min)**
- Tally all cash received in the prior month by channel (retail, DTC, foodservice)
- Tally all cash out in the prior month by category (production, ingredients, packaging, marketing/sampling, shipping)
- Calculate gross margin by channel: (revenue - COGS) / revenue
- Compare to prior month — is margin improving, stable, or declining?
- 30/60-day forecast: what's expected in (open invoices + anticipated DTC) vs. what's expected out (next production run, ingredient order, any planned marketing spend)?

**Step 5 — Quarterly financial review (see `03-operating-cadence.md`)**
- 3-month revenue by channel vs. plan
- Gross margin trend
- Cash position trend — is the business accumulating cash or drawing it down?
- BDC conversation readiness: do the numbers support a capital conversation? What would the capital be used for?

---

## 6. Cadence

**Weekly:**
- Monday cash scan: bank balance, AR aging, upcoming outflows (15 min)
- Any overdue invoices followed up within 24 hours of becoming overdue

**Monthly:**
- Full cash flow review: revenue by channel, costs by category, margin by channel, 30/60-day forecast
- AR aging reconciled against account log in `system-retail-velocity-engine.md`

**Quarterly:**
- Full financial review as part of operating cadence
- Channel margin comparison — which channel has the best economics at current volume?
- Capital assessment — is the business generating enough cash to self-fund growth, or is external capital worth exploring?

---

## 7. Tools & Data Sources

| Tool | Purpose |
|---|---|
| Invoicing tool (Wave, QuickBooks Simple Start, or Google Sheets — TBD) | Invoice creation, AR tracking, aging report |
| Bank account (online banking) | Actual cash position — checked weekly |
| Shopify | DTC revenue and payout schedule |
| Google Sheet (Cash Flow Model) | Monthly cash in/out summary, 30/60-day forecast, channel margin calculations |
| Account reorder log | Cross-reference for retail invoice status |

*Note: At current scale, a free tool like Wave Accounting covers invoicing, basic AR tracking, and expense logging without a monthly fee. QuickBooks Simple Start adds automation and bank reconciliation if volume warrants it. Decide by end of Q2 which tool to standardize on.*

---

## 8. Interfaces With Other Systems

**Reads from:**
- `system-retail-velocity-engine.md` — retail delivery events trigger invoices
- `system-dtc-funnel.md` — DTC revenue (Shopify payouts)
- `system-production-copacker.md` — production run costs (COGS inputs)
- `system-inventory-management.md` — ingredient purchase costs

**Writes to:**
- `02-company-goals-okrs.md` — revenue by channel, gross margin KPIs
- `01-strategy-2026-roadmap.md` (BDC note) — cash position informs capital conversation readiness
- `system-data-schema.md` — financial data structure feeds the master data model

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Days sales outstanding (DSO) | Average days to collect payment after invoice date | Monthly | Under 35 days |
| AR over 60 days | Value of invoices unpaid past 60 days | Monthly | Zero (flag immediately) |
| Gross margin — retail | (Retail revenue - COGS) / Retail revenue | Monthly | Document baseline; improving trend |
| Gross margin — DTC | (DTC revenue - COGS - shipping) / DTC revenue | Monthly | Higher than retail; document baseline |
| Gross margin — foodservice | (Foodservice revenue - COGS) / Foodservice revenue | Monthly | Document baseline |
| Monthly net cash flow | Cash in - cash out for the month | Monthly | Positive; growing trend |
| Cash runway | Months of operating costs covered by current cash | Monthly | Minimum 3 months at all times |
| Revenue by channel (monthly) | Retail / DTC / foodservice split | Monthly | All three growing; DTC growing fastest |

---

## 10. AI Opportunities

**Cash flow forecast generator:**
Give Claude the open AR aging report, anticipated DTC payout schedule, and planned outflows (next production run, ingredient order). Ask it to generate a 30/60-day cash flow forecast with a plain-language summary of any risk periods. Faster than building it manually in a spreadsheet.

**Invoice drafting:**
Give Claude the account name, order details (quantity, SKU, unit price), payment terms, and delivery date. Ask it to generate a formatted invoice ready for PDF export. Useful when volume picks up and invoicing becomes time-consuming.

**Overdue invoice follow-up email:**
Give Claude the account name, invoice number, amount, and days overdue. Ask it to draft a polite but direct follow-up email in Kris's voice. Removes the discomfort of writing a collections email from scratch.

**Monthly financial narrative:**
Paste the monthly cash flow numbers into Claude. Ask: "Write a 150-word plain-language summary of this month's financial performance for Kris to review and share with Evan." Turns a spreadsheet into a decision-ready summary.

**Margin improvement scenarios:**
Give Claude the current COGS, pricing, and channel mix. Ask: "What are three ways to improve gross margin by 5 percentage points without changing the product or the price?" Useful for the quarterly financial review conversation.
