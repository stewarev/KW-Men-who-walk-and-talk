# System: Production & Co-Packer

*Last updated: May 2026 | Owner: Kris | Review cadence: Per-run review, Quarterly SOP update*

---

## 1. Purpose

Maintain the quality and consistency of the hand-smoked Phlippens product across every production run — whether produced by Kris directly or supported by a co-packer — while building enough process documentation that production is not entirely dependent on one person's knowledge. The hand-smoked process is the brand's core quality story and its primary imitation barrier. This system protects it.

---

## 2. Scope

**In scope:**
- Production run planning and scheduling
- Hand-smoked process execution (garlic and onion smoking with fruitwood)
- Jarring, labelling, and quality checks
- Co-packer relationship management (if/when a co-packer is engaged to support volume)
- Production SOP documentation and version control
- Food safety and regulatory compliance (Ontario Food Safety Act requirements)

**Out of scope:**
- Ingredient procurement (covered in `system-inventory-management.md`)
- Delivery and fulfillment logistics (covered in `system-retail-velocity-engine.md` and `system-dtc-funnel.md`)
- New product development ideation (covered in `01-strategy-2026-roadmap.md` guardrails)

---

## 3. Inputs

- **Production trigger** from `system-inventory-management.md` — when finished goods fall below the reorder threshold, a production run is initiated
- **Demand forecast** — expected orders by channel over the next 6–8 weeks
- **Ingredient availability** — confirmed stock on hand before the run begins (garlic, onions, fruitwood, jars, lids, labels)
- **Production SOP** — documented step-by-step process for the hand-smoked method (see Section 5)
- **Co-packer capacity** — if using a co-packer, confirmed available dates and any lead time requirements on their end
- **Quality benchmarks** — target smoke profile, texture, flavour consistency, and fill level

---

## 4. Outputs

- **Completed production run log** — date, batch size, any process deviations, quality notes
- **Finished goods handoff** — units transferred to the inventory log in `system-inventory-management.md`
- **Ingredient replenishment flag** — any inputs that need reordering after the run
- **Quality flag** — any batch that doesn't meet the benchmark gets flagged before it ships; disposition decision documented
- **Updated SOP** — if the run revealed a process improvement, update the SOP version before the next run

---

## 5. Workflow

### Production SOP Overview (to be documented in full in a separate SOP file)

The hand-smoked process is the brand. These steps represent the non-negotiables:

1. **Prep** — select and prep garlic and onions to spec (size, freshness, Ontario-sourced where available)
2. **Smoking** — smoke with fruitwood at the established temperature and duration. Smoke profile is the key quality variable. Any deviation is noted.
3. **Processing** — blend or process smoked product to the target texture profile
4. **Quality check** — taste, texture, and colour check before jarring. Any batch that deviates from the benchmark is held for Kris's decision.
5. **Jarring** — fill to spec, seal, and label. Fill level and label placement quality checked.
6. **Final check** — sealed jars inspected for integrity. Any damaged seals pulled.
7. **Handoff to inventory** — batch logged with date, size, and quality notes.

### Production Run Planning

**Step 1 — Receive production trigger (from inventory system)**
When `system-inventory-management.md` flags that stock is at the reorder threshold, confirm:
- How many units are needed to restore to the target buffer?
- When is the next high-demand period (tasting event, seasonal peak)?
- Is ingredient stock sufficient for the required run size?

**Step 2 — Schedule the run**
- Minimum 2 weeks lead time from trigger to finished goods (accounts for ingredient sourcing, run time, and labelling)
- Co-packer coordination: if using a co-packer, confirm available dates with at least 3 weeks notice
- Add run date to the shared calendar — block production days

**Step 3 — Pre-run ingredient check**
Cross-reference ingredient inventory log against required quantities for the run. Source anything that's below threshold before the run date.

**Step 4 — Execute the run**
Follow the documented SOP. Log any deviations (temperature variance, timing change, ingredient substitution) in the run log. Even small deviations matter — they're the difference between a consistent product and a quality drift that damages accounts.

**Step 5 — Quality check and handoff**
- Taste and visual check on a sample from the batch
- Confirm fill levels and label quality
- Pass or hold decision made before any units leave production
- Units transferred to finished goods inventory log with batch date, quantity, and quality rating

**Step 6 — Run retrospective (30 min)**
- What worked? What was harder than it needed to be?
- Any process improvement to capture in the SOP?
- Was the run the right size, or does the demand signal need to be recalibrated?

---

## 6. Cadence

**Per-run:**
- Pre-run check: ingredients, SOP review, co-packer confirmation if applicable
- Post-run: batch log, quality notes, inventory handoff, SOP update if needed

**Monthly:**
- Review production run frequency vs. demand — are we running the right number of runs per month?
- Ingredient supplier performance — lead times, quality, any backup supplier needed?

**Quarterly:**
- SOP review — has the process evolved? Is the documentation still accurate?
- Co-packer relationship review — if a co-packer is being used, is the relationship working? Quality maintained? Capacity adequate?
- Seasonal demand planning — pre-build stock before summer and holiday peaks

### Co-Packer Engagement Criteria

Phlippens is currently produced by Kris directly. A co-packer should only be engaged when:
1. Demand consistently exceeds what Kris can produce alone in a reasonable number of hours per week
2. A co-packer can execute the hand-smoked process without compromising the core quality story
3. The economics of co-packing improve (not just maintain) margins at the target volume

**Non-negotiable co-packer requirements:**
- Must be able to execute the fruitwood smoking step — not substitute with liquid smoke or alternative methods
- Must be Ontario-based (Ontario provenance is part of the brand story)
- Must have appropriate food safety certifications (Ontario Food Safety Act)
- Kris must be able to do an unannounced quality visit at any time

---

## 7. Tools & Data Sources

| Tool | Purpose |
|---|---|
| Production run log (Google Sheet or Notion) | Date, batch size, quality notes, ingredient lot tracking |
| SOP document (separate file, version-controlled) | Step-by-step production process — updated after any change |
| Ingredient inventory log | Pre-run check and post-run replenishment flag |
| Shared calendar (Google) | Production run dates blocked for Kris |
| Co-packer contact and agreement | Relationship terms, pricing, lead time requirements, quality expectations |

---

## 8. Interfaces With Other Systems

**Reads from:**
- `system-inventory-management.md` — production trigger, required batch size
- Ingredient inventory (part of inventory management) — pre-run ingredient availability

**Writes to:**
- `system-inventory-management.md` — finished goods handoff after each run
- `system-ar-cashflow.md` — production cost per run (COGS input)
- `02-company-goals-okrs.md` — zero stockout KR, production SOP completion KR

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Batch quality pass rate | % of batches that pass quality check without hold or rework | Per run | 100% — any hold is a process flag |
| Run lead time | Days from production trigger to finished goods in inventory | Per run | Under 14 days |
| Units per run | Output per production run | Per run | Document baseline; track for scaling decisions |
| COGS per unit | Cost of ingredients + labour per finished jar | Monthly | Documented; improving trend as volume scales |
| Production hours (Kris) | Hours Kris spends on production per month | Monthly | Tracked for key person risk assessment |
| SOP currency | Is the SOP up to date with the actual process? | Quarterly | Yes — any deviation documented within 48 hours |

---

## 10. AI Opportunities

**Production run planner:**
Give Claude the current inventory snapshot, the demand forecast, and the production run log from the last 3 months. Ask it to suggest the optimal run size and timing for the next run, factoring in upcoming tasting events and seasonal peaks. Useful for pre-season planning.

**Co-packer RFQ template:**
When ready to explore co-packing, give Claude the SOP overview, volume estimates, and quality requirements. Ask it to draft a Request for Quote document to send to prospective co-packers. Saves hours of format research.

**SOP first-draft writing:**
Kris describes the production process step by step in plain language or voice note transcript. Claude structures it into a formal SOP document with version number, date, and step-by-step format. Converts tacit knowledge into documentation.

**Batch log summarizer:**
After a production run, paste quick notes into Claude and ask it to format them as a structured batch log entry. Keeps records consistent without requiring Kris to write formally after a long production day.
