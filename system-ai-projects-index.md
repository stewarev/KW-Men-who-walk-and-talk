# System: AI Projects Index

*Last updated: May 2026 | Owner: Evan | Review cadence: Monthly — add new projects as they emerge, archive completed or deprioritized ones*

---

## 1. Purpose

Track every active, planned, and completed AI project at Phlippens in one place. An AI project is any recurring or one-time use of Claude (or another AI tool) that produces a meaningful business output — not casual chat, but structured work with an input, a process, and a reusable output. This index prevents duplication, captures what's working, and builds an institutional memory of how Phlippens uses AI to move faster with a small team.

This document also serves as the prompt library — the place where the best prompts for each use case are documented so they can be reused without starting from scratch.

---

## 2. Scope

**In scope:**
- Recurring AI tasks (content drafting, monthly report generation, account outreach, financial summaries)
- One-time AI projects (SOP documentation, competitive briefs, campaign plans, schema design)
- AI-assisted analysis (funnel gap diagnosis, data interpretation, OKR scoring)
- Prompt templates that have been tested and work reliably

**Out of scope:**
- Casual AI conversations that don't produce a reusable output
- AI tools that Phlippens hasn't yet adopted (noted in the "Future" section for reference)
- Automated agents or scheduled tasks (tracked separately in the scheduling system)

---

## 3. Project Status Definitions

| Status | Meaning |
|---|---|
| **Active** | This project runs regularly and is producing value |
| **Planned** | Defined and ready to start; not yet running |
| **In progress** | A one-time project currently being worked on |
| **Completed** | One-time project done; output archived |
| **Paused** | Deprioritized; not running but not abandoned |
| **Archived** | No longer relevant; kept for reference |

---

## 4. Active AI Projects

---

### AI-001 — Weekly Content Draft

**Status:** Active
**Owner:** Evan
**Cadence:** Weekly (Monday)
**System:** `system-content-engine.md`
**Input:** Week's content focus (pillar + hook), one real story from the week (voice note or bullet points from Kris)
**Output:** 3 caption options (Phlippens voice + MWWT voice), Reel structure if applicable, subject line options for email if it's an email week
**Tool:** Claude (Cowork mode)

**Prompt template:**
```
You are writing Instagram captions for Phlippens, a hand-smoked Ontario condiment brand, and Men Who Walk & Talk, a men's community walking group in Waterloo Region.

This week's focus pillar is: [PILLAR — e.g., Recipe / Community / Product]
Hook idea: [ONE LINE HOOK OR STORY THREAD]
Real story detail from this week: [KRIS'S NOTES OR VOICE NOTE TRANSCRIPT]

Brand voice — Phlippens: warm, direct, slightly cheeky, never corporate. Talks like a person, not a brand.
Brand voice — MWWT: honest, low-pressure, bloke-ish. "No pressure. Just blokes & conversation."

Please write:
1. Three caption options for Phlippens Instagram (150 words max each, with a clear hook in the first line)
2. One caption option for MWWT Instagram if the content is community-relevant
3. If this is a Reel, a simple 3-5 beat visual structure for filming
4. Two subject line options if this is also an email week
```

**What's working:** Cuts caption drafting from 45 minutes to 10. Kris edits for his specific voice — about 15 minutes of review.
**What to watch:** Voice drift — if Claude starts sounding too polished or marketing-generic, add a "raw and honest, not slick" instruction.

---

### AI-002 — Monthly Performance Summary

**Status:** Active
**Owner:** Evan
**Cadence:** Monthly (first Monday of each month)
**System:** `system-content-engine.md`, `system-dtc-funnel.md`
**Input:** Instagram Insights export (top posts by reach and engagement), Klaviyo monthly report (open rate, click rate, new subscribers), brief notes on what happened in the month
**Output:** Plain-language summary of what worked, what didn't, and one recommended change for next month. Max 300 words.
**Tool:** Claude (Cowork mode)

**Prompt template:**
```
Here is Phlippens' content and email performance data for [MONTH]:

Instagram top posts:
[PASTE TOP 3 POSTS WITH REACH, SAVES, ENGAGEMENT RATE]

Instagram overall:
- Reels average reach: [X]
- Static posts average engagement rate: [X%]
- Profile visits: [X]
- Bio link clicks: [X]

Klaviyo:
- List size: [X]
- Monthly email open rate: [X%]
- Monthly email click rate: [X%]
- Welcome sequence conversion: [X%]
- New subscribers: [X]

Context notes: [ANYTHING UNUSUAL — tasting event, golf tournament, new product, etc.]

Please summarize:
1. What's working and why (2-3 observations)
2. What underperformed and a likely diagnosis (1-2 observations)
3. One specific change to make next month
Keep it under 300 words. Plain language, not consultant-speak.
```

---

### AI-003 — Account Tier Review & Tasting Schedule

**Status:** Active
**Owner:** Kris (data) + Evan (prompt)
**Cadence:** Monthly
**System:** `system-retail-velocity-engine.md`
**Input:** Full account reorder log (account name, last order date, estimated volume, placement quality, tier)
**Output:** Suggested tier assignments for next month, top 5 accounts to prioritize for tastings, any accounts to flag for a conversation about fit
**Tool:** Claude (Cowork mode)

**Prompt template:**
```
Here is Phlippens' current retail account log for [MONTH] tiering review:

[PASTE ACCOUNT TABLE: name, last order date, estimated reorder frequency, placement quality (counter/shelf/none), current tier]

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

### AI-004 — Klaviyo Email Draft (Monthly Broadcast)

**Status:** Active
**Owner:** Evan
**Cadence:** Monthly (last week of each month)
**System:** `system-dtc-funnel.md`, `system-content-engine.md`
**Input:** The month's best story (from the trail, the table, a retailer, a walk), any upcoming events, the CTA for this email (buy / walk sign-up / recipe)
**Output:** Full email draft: subject line options, body copy (150–200 words), CTA button text
**Tool:** Claude (Cowork mode)

**Prompt template:**
```
Write a Phlippens monthly email for [MONTH].

Brand voice: warm, direct, honest, slightly cheeky. Like a note from a person, not a newsletter from a brand. Max 200 words body.

The main story this month: [2-3 SENTENCES DESCRIBING THE STORY — trail, table, retailer, walk, event]
Upcoming: [ANY EVENTS, WALKS, OR SEASONAL MOMENTS IN THE NEXT 30 DAYS]
This month's CTA: [SINGLE CTA — buy four-pack / sign up for walk / try this recipe]
Bundle prices: four-pack $34.99 / twelve-pack $99.99 (use if purchase CTA)

Please write:
1. Three subject line options (one curiosity, one direct, one personal)
2. Email body (150-200 words)
3. CTA button text (5 words max)
4. One-line preview text (the text that shows under the subject line in the inbox)
```

---

### AI-005 — Cash Flow Forecast

**Status:** Active
**Owner:** Kris (data) + Evan (prompt)
**Cadence:** Monthly
**System:** `system-ar-cashflow.md`
**Input:** Open AR aging (account, invoice amount, due date), anticipated DTC payouts (Shopify average weekly), planned outflows (production run, ingredient order, marketing costs)
**Output:** 30/60-day cash flow forecast with plain-language risk summary
**Tool:** Claude (Cowork mode)

**Prompt template:**
```
Please generate a 30/60-day cash flow forecast for Phlippens.

Open accounts receivable (retail/foodservice):
[PASTE: account name, invoice amount, due date, days outstanding]

Anticipated DTC revenue:
- Average weekly Shopify payout: $[X]
- Next payout expected: [DATE]

Planned outflows in the next 60 days:
[LIST: production run cost, ingredient purchase, any marketing spend, shipping costs, other]

Current bank balance: $[X]

Please:
1. Show a week-by-week cash position for the next 8 weeks
2. Flag any weeks where cash could go below $[MINIMUM THRESHOLD]
3. Summarize in 3 sentences: comfortable / tight / at risk, and what to do about it
```

---

## 5. Planned AI Projects

---

### AI-006 — SOP Documentation (Production)

**Status:** Planned
**Owner:** Kris
**Trigger:** Before any co-packer conversation; before Q3 2026
**System:** `system-production-copacker.md`
**Description:** Kris describes the hand-smoked production process in a 20-minute voice note or structured conversation. Claude structures it into a formal SOP document with version number, step-by-step format, quality benchmarks, and decision points. Result saved as `sop-production-v1.md`.

**Prompt template (draft):**
```
I'm going to describe our production process for Phlippens hand-smoked condiment. Please structure what I tell you into a formal Standard Operating Procedure (SOP) with:
- Version number and date
- Purpose and scope
- Required equipment and ingredients (with specs)
- Step-by-step process (numbered, with decision points and quality checks called out)
- Quality benchmarks (what a passing batch looks and tastes like)
- Common failure modes and how to handle them

Here is the process as I'd describe it to someone doing it for the first time:
[KRIS'S DESCRIPTION]
```

---

### AI-007 — Competitive Brief (Local Market)

**Status:** Planned
**Owner:** Evan
**Trigger:** Before Q3 2026 strategy review
**System:** `01-strategy-2026-roadmap.md`
**Description:** Use Claude + web search to build a brief on the craft condiment competitive landscape in Ontario. Who else is in specialty retail in KW? What's the positioning? Where are the gaps? Output: 1-page competitive brief for the quarterly strategy review.

---

### AI-008 — DTC Funnel Audit

**Status:** Planned
**Owner:** Evan
**Trigger:** 90 days after Klaviyo welcome sequence goes live
**System:** `system-dtc-funnel.md`
**Description:** Paste 3 months of funnel data (sign-ups, open rates, click rates by email, conversion, repeat rate) and ask Claude to identify where the biggest drop-off is and what to test next. Output: funnel audit with 2–3 prioritized experiments.

---

### AI-009 — Media Pitch Draft

**Status:** Planned
**Owner:** Evan
**Trigger:** Before golf tournament (Week 5 of campaign)
**System:** `system-content-engine.md`
**Description:** Draft a media pitch for local KW press (Waterloo Region Record, CityNews Kitchener) using the community story angle — the KWSP golf tournament + Phlippens + MWWT as a human interest story about men and mental health, not a product launch. Output: 200-word pitch email with subject line.

---

## 6. Completed AI Projects

| ID | Project | Output | Date completed |
|---|---|---|---|
| AI-C001 | Blue Ocean Strategy analysis — Phlippens ecosystem | Ecosystem architecture (4 layers), ERRC grid, imitation barriers analysis | May 2026 |
| AI-C002 | StoryBrand SB7 framework application | Full SB7 map for Phlippens and MWWT | May 2026 |
| AI-C003 | Campaign plan — Take the Lid Off (v1 + v2) | `phlippens-ecosystem-campaign-plan.md` | May 2026 |
| AI-C004 | Company OS — Strategy, OKRs, Cadence docs | `01-strategy-2026-roadmap.md`, `02-company-goals-okrs.md`, `03-operating-cadence.md` | May 2026 |
| AI-C005 | Company OS — System docs (all 7 domains) | `system-retail-velocity-engine.md` through `system-ai-projects-index.md` | May 2026 |

---

## 7. AI Tools in Use

| Tool | Use cases | Notes |
|---|---|---|
| Claude (Cowork mode) | All active projects above — content, analysis, documents, forecasts | Primary AI tool. Cowork mode has access to workspace files. |
| Klaviyo AI (if available) | Subject line suggestions, send time optimization | Check if available on current Klaviyo plan |
| Shopify AI (Sidekick) | Order analysis, product description suggestions | Available on Shopify plans — explore |

**Not yet in use (evaluate in H2 2026):**
- A scheduling or automation tool (Zapier, Make) for low-complexity recurring tasks
- A transcription tool (Otter.ai, Fathom) for meeting notes and voice-to-text for production logs
- An image generation tool for social content mockups

---

## 8. Interfaces With Other Systems

**Reads from:** Every other system document — this index is the aggregation of all AI use cases across the Company OS.

**Writes to:**
- `03-operating-cadence.md` — monthly AI session is a standing cadence item
- `02-company-goals-okrs.md` — AI project outputs feed KPI tracking and OKR evidence

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Active AI projects | Number of AI projects running at regular cadence | Monthly | 4–6 active; not more than the team can maintain |
| Hours saved estimate | Rough estimate of hours saved by active AI projects per month | Monthly | Track qualitatively — "this saved X hours" in monthly note |
| Output quality rating | Kris's rating of AI-drafted content that went live (1–5) | Monthly | 4+ average; any 2 or below triggers prompt review |
| New projects added | AI use cases identified and added to the index | Quarterly | At least 2 new projects per quarter |

---

## 10. Prompt Hygiene Rules

1. **Always include the brand voice definition** in any content prompt. Without it, Claude defaults to generic marketing tone.
2. **Specify the output format explicitly.** "Three caption options" is better than "write some captions."
3. **Include real context, not hypotheticals.** "The tasting at Vincenzo's last Tuesday had 40 people try the sauce" produces better content than "we ran a tasting."
4. **Set a word count or length constraint** on any writing task. No constraint = rambling output.
5. **Review the output before sharing with Kris.** Claude's first draft is a starting point, not a final product.
6. **Save prompts that work.** When a prompt produces a great output, paste both into this index. The prompt is an asset.
7. **Name your sessions.** In Cowork mode, describe the task clearly at the start. "Phlippens weekly content — Week 3 of the Take the Lid Off campaign, recipe pillar, restaurant story hook" beats "write some posts."
