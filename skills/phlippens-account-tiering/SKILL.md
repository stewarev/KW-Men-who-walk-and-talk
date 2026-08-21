---
name: phlippens-account-tiering
description: "Runs the monthly Phlippens retail account tiering review. Use this skill when the user pastes an account reorder log and asks for tier assignments, when they say 'time for the monthly tiering', 'tier the accounts', 'which accounts need tastings this month', 'account review', 'help me prioritize the stores', or anything related to figuring out which retail accounts are A/B/C and what support each needs. Also trigger when the user mentions the tasting schedule, flags inactive accounts, or asks 'who should Kris visit this month.' This skill knows the A/B/C criteria, the tasting scheduling logic, and how to flag at-risk accounts — always use it rather than doing the tiering manually."
---

# Phlippens Account Tiering Skill

This skill runs the monthly retail account tiering review for Phlippens. It takes the current account reorder log and available scheduling context, and outputs tier assignments, a prioritized tasting list, at-risk account flags, and a rough tasting schedule — cutting the manual sort from 30+ minutes to under 10.

Phlippens has 50+ active reordering accounts in Waterloo Region. The goal of this system is depth, not breadth — turning the existing footprint into a velocity asset by making sure the right stores get the right support at the right time.

---

## What You Need to Run This

Before running the review, collect:

1. **Account reorder log** — paste the table: account name, last order date, estimated reorder frequency (or days since last order), placement quality (counter / end cap / standard shelf / none), current tier (or "untiered" if first run), any relationship notes
2. **Tasting availability** — which dates and days Kris is available for tastings this month
3. **Sampling inventory** — how many units are available for in-store tastings
4. **Upcoming calendar events** — golf tournament, MWWT walks, seasonal moments (summer grilling, holiday gifting). These affect which accounts to prioritize and when.

If the user hasn't provided the account log, ask for it. The rest can be estimated if needed, but the account log is required.

---

## The A/B/C Tiering System

Tier each account on two axes: **current performance** (how fast are they reordering?) and **potential** (is there room to grow?).

### Tier A — Prioritize and Activate
- High reorder frequency (reordering within 3–4 weeks consistently)
- Featured placement: counter, end cap, or visible signage — not buried on a shelf
- Owner is engaged: knows the product, talks it up, responds to Kris
- **Support:** Monthly in-person visit. Priority for tasting support. These accounts compound — protect and invest here.

### Tier B — Maintain and Grow
- Moderate reorder frequency (reordering, but cycle is longer or inconsistent)
- Standard shelf placement, or placement that could be improved with a conversation
- Owner is responsive but not proactively promoting
- **Support:** Quarterly tastings. Monthly check-in call or delivery touchpoint. Upgrade candidates: flag B accounts where a tasting or placement ask could move them to A.

### Tier C — Assess Honestly
- Low reorder frequency (60+ days between orders, or inconsistent pattern)
- Poor placement (back shelf, not visible, or hard to find)
- Low owner engagement — no relationship built
- **Support:** 60-day check-in. Honest assessment of whether the relationship is worth continuing. These accounts absorb time and inventory for low return — it's OK to let them go if the fit isn't there.

**Placement quality scoring for the sort:**
- Counter / end cap / dedicated display = High potential
- Mid-shelf, visible = Moderate
- Bottom shelf, back corner, or no permanent home = Low

---

## Output Format

Produce the following, in this order:

### 1. Tier Assignment Table
For each account in the log, assign a tier (A / B / C) with a one-line rationale:

| Account | Current Tier | Suggested Tier | Rationale |
|---------|-------------|----------------|-----------|
| Vincenzo's | B | A | Reordering every 3 weeks, counter placement, owner actively recommends |
| [Account] | [Old] | [New] | [Why] |

Flag any accounts that are moving tiers (up or down) — these are the most important for Kris to notice.

### 2. Top 5 Tasting Priorities
List the top 5 accounts to prioritize for in-store tasting support this month. For each, explain why it's on the list:
- Is it an A account due for regular support?
- A B account with upgrade potential?
- A high-foot-traffic moment coming up (seasonal, nearby event)?
- An account that recently had a gap in support?

Order by priority. Give Kris enough context to say yes or no to each quickly.

### 3. At-Risk Account Flags
List any accounts that haven't reordered in 60+ days, or show a meaningful drop in reorder frequency compared to earlier in the year. For each, suggest one of:
- **Reach out now** — relationship worth saving, probably just needs a touchpoint
- **Schedule a conversation** — fit might not be right, worth a frank talk about what's working
- **Let it go** — low velocity, poor placement, low owner engagement; cost of support outweighs return

### 4. Proposed Tasting Schedule
Given the available dates, top 5 priority accounts, and inventory on hand, propose a rough tasting schedule for the next 4–6 weeks:

| Date | Account | Notes |
|------|---------|-------|
| [Date] | [Account] | [Any context — near event, seasonal hook, bring story cards] |

Keep it realistic for a 2-person team. One or two tastings per week maximum unless it's a campaign peak week.

---

## Tiering Logic Notes

**Reorder frequency benchmarks:**
- Excellent: reordering every 2–3 weeks
- Good: every 4–5 weeks
- Slow: every 6–8 weeks
- At risk: 60+ days, or hasn't reordered since last tiering

**Don't punish new accounts.** An account that's only had the product for 6 weeks shouldn't be C-tiered just because they haven't reordered a third time. Note "new" in the rationale and give them one more cycle.

**Seasonality matters.** A summer-grilling account that slows in January isn't C-tier — it's seasonal. Flag seasonality in the rationale rather than downgrading.

**Placement upgrades are the fastest lever.** A B account with strong reorder frequency but shelf placement is often one conversation away from A. Flag these as "placement upgrade priority" — a tasting conversation is the natural moment to make that ask.

---

## Prompt Template (for reference / manual use)

If running outside the skill:

```
Here is Phlippens' current retail account log for [MONTH] tiering review:

[PASTE ACCOUNT TABLE: name, last order date, estimated reorder frequency,
placement quality (counter/end cap/shelf/none), current tier, any notes]

Tasting availability this month: [DATES AND DAYS AVAILABLE]
Inventory available for sampling: [X UNITS]
Upcoming events to factor in: [GOLF TOURNAMENT / MWWT WALK / SEASONAL MOMENT]

Please:
1. Suggest a tier (A/B/C) for each account based on reorder frequency and placement quality
2. Identify the top 5 accounts for tasting support this month and explain why
3. Flag any accounts at risk of going inactive (no order in 60+ days)
4. Propose a rough tasting schedule across the available dates
```

---

## What to Watch

**Don't over-engineer C decisions.** Kris has relationships with these owners — a C-tier flag is information for a conversation, not an automatic exit. Present the flag, note the data, let Kris decide.

**Tasting inventory is the real constraint.** If sampling stock is low, fewer tastings. Better to do two excellent tastings with real story-telling than five thin ones where the product runs out early.

**The golf tournament (Week 7 of the Take the Lid Off campaign) is a key activation moment.** In the months leading up to it, flag accounts near golf courses, country clubs, or event venues as elevated priority.

**Keep the schedule to what Kris can actually do.** He runs production, sales, and delivery. Two tastings per week is a lot on top of that. One excellent tasting per week is often the right answer.
