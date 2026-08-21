# System: Data Schema

*Last updated: May 2026 | Owner: Evan | Review cadence: Quarterly — update when a new system or data source is added*

---

## 1. Purpose

Define the master data model for Phlippens — what data exists, where it lives, what it means, and how the different data sources connect to each other. This document is not a database spec; it is a shared understanding of the company's data landscape. It exists so that when Claude (or any future tool) is asked to analyze data, interpret KPIs, or build a report, the definitions are unambiguous and the sources are known. It also surfaces the gaps — data that should exist but doesn't yet — so they can be planned for.

Good data at this stage doesn't require sophisticated tools. It requires consistent definitions, consistent capture, and consistent storage. This schema defines all three.

---

## 2. Scope

**In scope:**
- Retail accounts data (accounts, orders, contacts, placement)
- DTC data (Shopify orders, customers, Klaviyo subscribers)
- Production data (batch logs, COGS, ingredient costs)
- Financial data (revenue by channel, AR, cash position)
- Marketing and content data (Instagram performance, email metrics)
- Community data (MWWT walk attendance, sign-ups)

**Out of scope:**
- Foodservice distributor data (not applicable at current stage)
- National retail scan data (not applicable until chain retail is pursued)
- Detailed consumer research data (managed separately in `system-content-engine.md` retrospectives)

---

## 3. Core Data Entities

### 3.1 Account (Retail & Foodservice)

The Account is the master record for every business Phlippens sells to or samples at. One record per location.

| Field | Definition | Source | Type |
|---|---|---|---|
| account_id | Unique identifier | Manual (auto-increment in Notion/Sheets) | String |
| account_name | Business name | Manual | String |
| account_type | Retail / Foodservice / Event | Manual | Enum |
| owner_name | Primary contact name | Manual | String |
| owner_email | Primary contact email | Manual | String |
| owner_phone | Primary contact phone | Manual | String |
| address | Full street address | Manual | String |
| city | City | Manual | String |
| region | Waterloo Region / Other | Manual | Enum |
| tier | A / B / C | `system-retail-velocity-engine.md` (monthly review) | Enum |
| placement_quality | Counter / End cap / Shelf / None | Manual (account visit) | Enum |
| first_order_date | Date of first order | Manual | Date |
| last_order_date | Date of most recent order | Manual or Shopify | Date |
| reorder_frequency_days | Average days between orders | Calculated | Integer |
| relationship_notes | Free text — owner personality, preferences, flags | Manual | Text |
| story_card_deployed | Story card currently at this location | Manual | Boolean |
| active | Is this account currently ordering? | Manual | Boolean |

---

### 3.2 Order (Retail & Foodservice)

One record per delivery or shipment to an account.

| Field | Definition | Source | Type |
|---|---|---|---|
| order_id | Unique identifier | Manual or invoicing tool | String |
| account_id | Links to Account record | Manual | FK → Account |
| order_date | Date order was placed or confirmed | Manual | Date |
| delivery_date | Date product was delivered | Manual | Date |
| sku | Product SKU (e.g., PHLIPPEN-ORIG-250ML) | Manual | String |
| quantity | Units in the order | Manual | Integer |
| unit_price | Price per unit at time of order | Manual | Decimal |
| total_value | quantity × unit_price | Calculated | Decimal |
| invoice_number | Invoice reference | Invoicing tool | String |
| payment_status | Unpaid / Paid / Overdue | Manual or invoicing tool | Enum |
| payment_date | Date payment received | Manual | Date |
| channel | Retail / Foodservice | Manual | Enum |

---

### 3.3 DTC Customer

One record per unique customer who has placed a DTC order through phlippens.com.

| Field | Definition | Source | Type |
|---|---|---|---|
| customer_id | Unique identifier | Shopify | String |
| email | Customer email | Shopify | String |
| first_name | First name | Shopify | String |
| city | City (from shipping address) | Shopify | String |
| first_order_date | Date of first DTC purchase | Shopify | Date |
| last_order_date | Date of most recent DTC purchase | Shopify | Date |
| total_orders | Lifetime order count | Shopify (calculated) | Integer |
| lifetime_value | Total revenue from this customer | Shopify (calculated) | Decimal |
| klaviyo_subscribed | Is this customer on the email list? | Klaviyo | Boolean |
| welcome_sequence_status | Not started / In progress / Completed | Klaviyo | Enum |
| acquisition_source | How did they find us? (IG / tasting / walk / referral / organic) | Klaviyo tag or manual | Enum |

---

### 3.4 DTC Order

One record per Shopify order.

| Field | Definition | Source | Type |
|---|---|---|---|
| shopify_order_id | Shopify order number | Shopify | String |
| customer_id | Links to DTC Customer | Shopify | FK → Customer |
| order_date | Date order placed | Shopify | Date |
| sku | Product SKU | Shopify | String |
| quantity | Units ordered | Shopify | Integer |
| bundle_type | Single / Four-pack / Twelve-pack | Shopify (product) | Enum |
| revenue | Total order value (before any discount) | Shopify | Decimal |
| discount_applied | Any discount code used | Shopify | String |
| net_revenue | Revenue after discount | Shopify | Decimal |
| shipping_cost | Actual shipping cost | Shopify | Decimal |
| payout_date | Date Shopify paid out | Shopify | Date |

---

### 3.5 Email Subscriber (Klaviyo)

One record per email address in the Klaviyo list.

| Field | Definition | Source | Type |
|---|---|---|---|
| email | Email address | Klaviyo | String |
| first_name | First name | Klaviyo | String |
| subscribe_date | Date added to list | Klaviyo | Date |
| subscribe_source | IG bio / tasting event / walk / QR card / referral | Klaviyo tag | Enum |
| list | Phlippens main / MWWT community | Klaviyo | Enum |
| welcome_sequence_completed | Has the 3-email sequence been completed? | Klaviyo | Boolean |
| has_purchased | Has this subscriber made at least one DTC purchase? | Klaviyo (Shopify integration) | Boolean |
| unsubscribed | Has this person unsubscribed? | Klaviyo | Boolean |

---

### 3.6 Production Batch

One record per production run.

| Field | Definition | Source | Type |
|---|---|---|---|
| batch_id | Unique batch identifier (date-based, e.g., BATCH-2026-05-15) | Manual | String |
| production_date | Date production run was completed | Manual | Date |
| sku | Product SKU produced | Manual | String |
| units_produced | Total units from this run | Manual | Integer |
| ingredient_cost | Total ingredient cost for this batch | Manual | Decimal |
| packaging_cost | Total packaging cost for this batch | Manual | Decimal |
| copacker_fee | Co-packer fees if applicable | Manual | Decimal |
| total_cogs | ingredient_cost + packaging_cost + copacker_fee | Calculated | Decimal |
| cogs_per_unit | total_cogs / units_produced | Calculated | Decimal |
| quality_rating | Pass / Hold / Rework | Manual | Enum |
| quality_notes | Free text — any deviations from SOP | Manual | Text |

---

### 3.7 Tasting Event

One record per in-store tasting or sampling event.

| Field | Definition | Source | Type |
|---|---|---|---|
| event_id | Unique identifier | Manual | String |
| event_date | Date of tasting | Manual | Date |
| account_id | Links to Account record | Manual | FK → Account |
| event_type | In-store tasting / Festival / Golf tournament / Walk | Manual | Enum |
| samples_distributed | Estimated number of samples given | Manual (tasting notes) | Integer |
| new_email_captures | New email sign-ups at the event | Manual | Integer |
| new_walk_signups | New MWWT sign-ups at the event (if applicable) | Manual | Integer |
| story_cards_distributed | Story cards handed out | Manual | Integer |
| reorder_delta | Change in account order volume in 30 days after vs. 30 days before | Calculated (from Order) | Decimal |
| notes | Free text — reactions, conversations, follow-ups needed | Manual | Text |

---

### 3.8 Community (MWWT Walk)

One record per MWWT walk event.

| Field | Definition | Source | Type |
|---|---|---|---|
| walk_id | Unique identifier (date-based) | Manual | String |
| walk_date | Date of walk | Manual | Date |
| location | Trail name and address | Manual | String |
| attendance | Number of men who showed up | Manual (sign-in) | Integer |
| new_attendees | First-time walkers | Manual | Integer |
| email_captures | Email addresses captured (for Klaviyo MWWT list) | Manual | Integer |
| content_captured | Was footage or photos taken? | Manual | Boolean |
| facebook_event_link | Link to the Facebook Event | Manual | String |
| notes | Anything notable — conversations, energy, follow-ups | Manual | Text |

---

## 4. Data Connections (How Entities Relate)

```
Account ──────────────── Order (retail/foodservice)
   │                        │
   └── Tasting Event ────── reorder_delta (calculated)
                               │
Email Subscriber ──────── DTC Customer ── DTC Order
   │                           │
   └── Welcome Sequence        └── Production Batch (COGS)
   
Walk Attendance ─────── Email Subscriber (MWWT list)
                              │
                         KPI Dashboard (02-company-goals-okrs.md)
```

---

## 5. Data Gaps (What Doesn't Exist Yet)

These are data points the business needs but doesn't currently capture. They should be built into the system as the corresponding workflow is set up.

| Gap | Why it matters | How to close it |
|---|---|---|
| Retail sell-through data | No visibility into how fast product moves off the shelf (only reorder data) | Ask top 10 accounts to share rough weekly sales; track anecdotally during visits |
| DTC acquisition source | Currently unknown which channel drives DTC buyers | Klaviyo UTM tags on Instagram bio link; tasting sign-up form asks "How did you hear about us?" |
| Foodservice order data | No formal tracking yet (one account) | Add foodservice to the Order schema as soon as the second account is opened |
| Customer satisfaction / NPS | No direct feedback loop from buyers | Add one-question email 30 days after first DTC purchase ("How was it?") |
| Ingredient cost per unit (documented) | COGS is estimated, not formally tracked | Production batch log — fill in ingredient and packaging costs per run |

---

## 6. Cadence

**Ongoing (per event):**
- New accounts added to Account table same day as first contact
- Orders logged same day as delivery
- Tasting events logged within 24 hours of completion
- Walks logged within 24 hours

**Monthly:**
- Data schema review: any new data sources added? Any fields that aren't being filled in consistently?
- Gap list review: has any gap been closed? Any new gap identified?

**Quarterly:**
- Full schema review: do the entities still reflect the business? Any new product, channel, or system that needs a new entity?
- Data quality audit: are the key fields (tier, last_order_date, email capture) being maintained?

---

## 7. Tools & Data Sources

| Entity | Where data lives | Format |
|---|---|---|
| Accounts | Notion database or Google Sheet | Table |
| Orders (retail/foodservice) | Invoice tool + same spreadsheet | Table |
| DTC Customers | Shopify + Klaviyo | Platform-native |
| DTC Orders | Shopify | Platform-native |
| Email Subscribers | Klaviyo | Platform-native |
| Production Batches | Google Sheet (production log) | Table |
| Tasting Events | Notion or Google Sheet | Table |
| MWWT Walks | Notion or Google Sheet | Table |
| KPI Dashboard | Google Sheet (master) | Table / calculated fields |

*Note: All manual tables should live in one place — either Notion or Google Sheets, not both. Decide on one and migrate everything to it by end of Q2 2026. Splitting data across two tools creates duplication and drift.*

---

## 8. Interfaces With Other Systems

This schema is the foundation that all other systems read from and write to.

**Reads from (data created by):**
- `system-retail-velocity-engine.md` → Account, Order, Tasting Event
- `system-dtc-funnel.md` → DTC Customer, DTC Order, Email Subscriber
- `system-production-copacker.md` → Production Batch
- `system-inventory-management.md` → Production Batch (ingredient costs)
- `system-ar-cashflow.md` → Order (payment status), financial summary

**Writes to (data consumed by):**
- `02-company-goals-okrs.md` → KPI table
- `system-ai-projects-index.md` → data available for AI analysis

---

## 9. AI Opportunities

**Schema maintenance agent:**
Once per quarter, paste the current schema and any new data sources or workflows into Claude. Ask: "What fields or entities are missing from this schema given the current state of the business?" Keeps the schema current without requiring a full audit every time something changes.

**Data gap prioritization:**
Paste the Gap table (Section 5) into Claude with the current business context. Ask: "Which of these data gaps is most likely to cause a bad decision in the next 90 days?" Prioritizes the data infrastructure work against strategic needs.

**Query assistant:**
Paste a data table (e.g., the account reorder log) into Claude and ask natural-language questions: "Which accounts haven't reordered in 60 days?" or "What's the average reorder frequency for A-tier accounts?" Removes the need for SQL or pivot tables at this stage.

**Report generator:**
Give Claude a raw data export (account log, Shopify order CSV, Klaviyo export) and ask for a plain-language summary with the top 3 insights and one recommended action. Turns data into decisions in minutes.
