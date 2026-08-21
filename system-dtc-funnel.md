# System: DTC Funnel

*Last updated: May 2026 | Owner: Evan (infrastructure) + Kris (product and story) | Review cadence: Monthly conversion review, Quarterly funnel audit*

---

## 1. Purpose

Turn Instagram followers, walk attendees, tasting event visitors, and retail customers into direct-to-consumer buyers at phlippens.com — and then into repeat buyers and brand advocates. The DTC funnel is the only channel where Phlippens owns the customer relationship fully. Every other channel (retail, foodservice, social) rents access to the customer. The email list and the purchase history in Shopify are owned assets that survive any algorithm change, retailer decision, or platform shift. This system builds and protects those owned assets, one purchase at a time.

---

## 2. Scope

**In scope:**
- Traffic from Instagram (recipe Reels, bio link)
- Email capture from all touchpoints (tasting events, walks, Instagram bio, story card QR codes)
- Klaviyo welcome sequence and monthly broadcast email
- Shopify order management and repeat purchase tracking
- Bundle pricing strategy ($34.99 four-pack, $99.99 twelve-pack)
- DTC-specific promotions (gifting campaigns, seasonal bundles)

**Out of scope:**
- Paid traffic acquisition (not until organic funnel is proven and unit economics support it)
- Wholesale/B2B orders through the website (treated as retail, managed in `system-retail-velocity-engine.md`)
- Subscription model (a future consideration, not in scope for 2026)
- Returns and customer service escalations beyond basic email response

---

## 3. Inputs

- **Content engine output** — recipe Reels and brand content that drive traffic and create intent to buy (`system-content-engine.md`)
- **Email sign-ups** — captured at tasting events, MWWT walks, Instagram bio link, story card QR codes
- **Shopify order data** — purchase history, repeat rate, average order value, SKU breakdown
- **Klaviyo data** — list size, welcome sequence open/click/conversion rates, monthly broadcast performance
- **Product inventory available for DTC** — confirmed stock set aside for direct orders (`system-inventory-management.md`)
- **Seasonal calendar** — gifting peaks (holiday), grilling season (summer), any promo moments

---

## 4. Outputs

- **Email list growth** — new subscribers captured from all touchpoints added to Klaviyo weekly
- **Welcome sequence conversions** — purchases attributed to the 3-email onboarding flow
- **Monthly DTC revenue** — orders placed through phlippens.com, broken out by SKU
- **Repeat purchase rate** — % of customers who buy again within 90 days
- **Monthly funnel report** — traffic, email sign-ups, conversion rate, AOV, repeat rate, revenue
- **Promo and gifting campaign assets** — copy and landing page updates for seasonal moments

---

## 5. Workflow

### The Funnel Map

```
AWARENESS
  Instagram recipe Reel / walk content / tasting event
        ↓
CAPTURE
  "Link in bio" → email sign-up landing page
  QR code on story card → same landing page
  MWWT walk sign-in → email added to list
        ↓
NURTURE (Klaviyo Welcome Sequence)
  Email 1: The restaurant anchor story — "A KW chef uses this by name. Here's why."
  Email 2: The recipe — "Here's what to make with it tonight."
  Email 3: The community — "Food sparks connection. Here's what we're building."
        ↓
CONVERSION
  CTA in Email 1 and Email 2 → phlippens.com → 4-pack at $34.99
  CTA in Email 3 → 12-pack at $99.99 (positioned as a gift)
        ↓
REPEAT
  Monthly broadcast email: story + recipe + soft purchase CTA
  Seasonal gifting campaign: 12-pack holiday gift push (November)
  Grilling season push: 4-pack summer promo (June–August)
        ↓
ADVOCACY
  DTC customer featured in KIPR content (with permission)
  "Share with a bloke" referral prompt in Email 3
```

---

### Key Workflows

**Email capture (ongoing)**

Every touchpoint has a capture mechanism:
- Instagram bio: link to sign-up landing page. Update if the link changes.
- Story card QR code: scans go to the same landing page. Test the QR code before each print run.
- Tasting events: pen-and-paper sign-up sheet at every tasting. Names and emails added to Klaviyo within 24 hours of the event.
- MWWT walks: walk sign-in sheet includes optional email field. Added to a separate MWWT list in Klaviyo, tagged for community content.

**Klaviyo setup (one-time, then maintain)**

Welcome sequence:
- Email 1 — sent immediately on sign-up. Subject: "A KW chef put this on the menu by name." 150 words. One image. One button: "Try it — four-pack, $34.99."
- Email 2 — sent 3 days after Email 1. Subject: "The recipe that started it all." One simple recipe using Phlippens. One button: "Get it delivered."
- Email 3 — sent 7 days after Email 1. Subject: "The table is where it happens." MWWT connection. Soft push for the twelve-pack as a gift for "the guys in your life."

Monthly broadcast (last week of each month):
- One story from the trail or the table
- One recipe or product use tip
- Upcoming events (walks, tastings)
- One CTA: buy, gift, or walk sign-up — pick one per send

**Shopify order management**
- All DTC orders fulfilled within 3 business days
- Shipping confirmation sent automatically through Shopify
- Any order with a personal note (gift, etc.) flagged for a handwritten insert if time allows
- Repeat customer orders tracked manually in the customer log until an automated report is set up

**Seasonal campaign activation**

| Season | Timing | Product | Message angle |
|---|---|---|---|
| Summer grilling | May launch, June–August peak | 4-pack | "The sauce a KW chef puts on the menu. Now on your grill." |
| Back to school / fall reset | September | 4-pack | Recipe content pivot to heartier dishes |
| Holiday gifting | Mid-November push | 12-pack | "For the guy who has everything — except this." |

---

## 6. Cadence

**Weekly:**
- Check Shopify orders — fulfilled within 3 business days?
- Any email sign-ups from the week's tasting or walk? Added to Klaviyo?
- Bio link working and pointing to the right page?

**Monthly:**
- Pull funnel report: sign-ups, welcome sequence conversion, monthly email metrics, DTC revenue
- Review repeat purchase rate — any customers who bought once and haven't returned? Segment for re-engagement.
- Confirm next month's email is planned and drafted
- Update landing page or bio link if a promo is starting

**Quarterly:**
- Full funnel audit: where do people drop off? Which email in the welcome sequence has the highest unsubscribe rate? Is the landing page converting?
- Seasonal campaign planning for the coming quarter
- AOV analysis: are customers buying one jar or bundling? Does the bundle pricing need adjustment?
- Welcome sequence refresh: is the restaurant anchor story still the lead? Any new social proof to add?

---

## 7. Tools & Data Sources

| Tool | Purpose |
|---|---|
| Shopify | Order management, purchase history, revenue by SKU |
| Klaviyo | Email list, welcome sequence, monthly broadcast, segmentation |
| Instagram | Primary traffic driver — recipe Reels and bio link |
| Sign-up landing page (Shopify or Klaviyo-hosted) | Email capture from all organic touchpoints |
| Story card QR code | Physical capture point — links to sign-up page |
| Google Analytics (optional) | Website traffic source analysis — useful once traffic is significant |

---

## 8. Interfaces With Other Systems

**Reads from:**
- `system-content-engine.md` — recipe Reels and content that drive funnel traffic
- `system-inventory-management.md` — available DTC stock; flag if DTC buffer drops below threshold
- `system-retail-velocity-engine.md` — tasting events generate email sign-ups
- `01-strategy-2026-roadmap.md` — DTC goals and bundle pricing strategy

**Writes to:**
- `system-ar-cashflow.md` — DTC revenue events feed accounts receivable and cash flow
- `02-company-goals-okrs.md` — DTC order KPIs, email list KPIs, repeat rate
- `system-ai-projects-index.md` — email copy, funnel analysis, and welcome sequence optimization are active AI projects

---

## 9. Metrics

| Metric | Definition | Frequency | Target |
|---|---|---|---|
| Email sign-ups (monthly) | New subscribers added to Klaviyo from all sources | Monthly | Growing trend; 150+ total by end of Q3 |
| Welcome sequence open rate | Email 1 opens / sends | Monthly | 45%+ |
| Welcome sequence conversion | Purchases from welcome sequence / subscribers who completed it | Monthly | 10%+ |
| Monthly DTC orders | Total orders placed through phlippens.com | Monthly | 25+/month by Q4 |
| Average order value (AOV) | Revenue / orders | Monthly | $34.99+ (four-pack as baseline) |
| Repeat purchase rate | Customers who buy again within 90 days | Monthly | 30%+ |
| Monthly email open rate | Opens / sends (broadcast) | Monthly | 35%+ |
| Monthly email click rate | Clicks / sends (broadcast) | Monthly | 5%+ |
| Unsubscribe rate | Unsubscribes / sends | Monthly | Below 0.5% per send |

---

## 10. AI Opportunities

**Welcome sequence copy:**
Give Claude the restaurant anchor story, the brand voice guidelines, and the three email briefs. Ask it to draft all three emails with subject line options, body copy, and CTA text. First draft in 10 minutes; Kris reviews for voice.

**Funnel gap diagnosis:**
Paste the monthly funnel metrics (sign-ups, open rates, click rates, conversion, repeat rate). Ask Claude: "Where is the biggest drop-off in this funnel and what are the most likely causes?" Gets a structured diagnosis without needing a conversion optimization consultant.

**Seasonal campaign planner:**
Give Claude the seasonal calendar and past performance data. Ask it to plan the gifting campaign: email sequence, timing, subject lines, and CTA copy for the twelve-pack holiday push.

**Re-engagement email:**
Identify customers who bought once but haven't returned in 90 days. Give Claude the customer profile (what they bought, when) and ask it to draft a re-engagement email: honest, warm, low-pressure, with a recipe or story as the hook rather than a discount.

**A/B subject line generator:**
For every email, give Claude the body copy and ask it to generate 5 subject line options in different styles (curiosity, direct, personal, story-led, question). Pick the best two and test if the list is large enough.
