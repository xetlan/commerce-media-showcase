# Commerce Media Performance Showcase

> **All figures are illustrative.** Numbers represent realistic relative magnitudes for a mid-to-large retailer at ~10M monthly sessions running Contentsquare DXA + Merchandising + Zoning Analysis + Session Replay + Sense AI. No real customer data is used. Worked example uses "Adidas" as a featured brand partner; spend, revenue, and engagement figures are fabricated for illustration.

A reference set of seven dashboards and reports a Contentsquare-instrumented retailer can deliver to brand partners to win and renew commerce media budgets, plus an instrumentation appendix specifying exactly what must be configured in Contentsquare to reproduce each view.

---

## Dashboard 1 — Brand Performance Cockpit (Adidas)

**Business question:** Is Adidas's commerce media spend on our platform performing, trending in the right direction, and competitive against category benchmarks?

**Sense AI headline**
> *Adidas sponsored revenue grew +18% MoM, driven primarily by search-carousel exposure on mobile. ROAS held steady at 3.9x despite a 12% increase in inventory served.*

**Headline KPIs — Last 30 days**

| Metric | Value | vs Prior 30 days | vs Athletic Footwear Benchmark |
|---|---:|---:|---:|
| Exposure sessions | 2,400,000 | +12.4% | n/a |
| Clicks | 83,400 | +14.1% | n/a |
| CTR (weighted) | 3.48% | +0.05 pp | +0.31 pp |
| ATC rate (of clicks) | 14.0% | +1.2 pp | +1.8 pp |
| Conversions | 4,578 | +21.6% | n/a |
| CR (of clicks) | 5.49% | +0.34 pp | +0.42 pp |
| Attributed revenue | $503,580 | +18.2% | n/a |
| Spend | $128,000 | +11.3% | n/a |
| **ROAS** | **3.93x** | **+0.18x** | **+0.4x** |
| Share-of-shelf (athletic footwear) | 27% | +3 pp | n/a |

**30-day trend (revenue, $ thousands per day)**

```
Day 1   ███████████████░░░░░░░░░░  $14.2k
Day 7   ████████████████░░░░░░░░░  $15.1k
Day 14  ██████████████████░░░░░░░  $17.0k
Day 21  ████████████████████░░░░░  $18.9k
Day 30  ██████████████████████░░░  $20.4k        ▲ +44% vs Day 1
```

**What to do with this**
- Renew Adidas Q3 inventory commitment at current pricing — performance trajectory and ROAS support a 10–15% rate uplift.
- Investigate mobile-search-carousel as a growth lever: it drove most of the MoM lift; explore extending Adidas creative refresh cadence there.
- Flag share-of-shelf to merchandising — at 27%, Adidas is approaching the internal 30% concentration ceiling for any single brand in athletic footwear.

**Data requirements:** Adidas brand tagged in Merchandising catalog; "Adidas exposure" segment built from Zoning click-zone exposure; goals for Reached PDP / Add to Cart / Reached Order Received; ecommerce APIs (Transaction, Add to Cart) populating revenue and AOV at SKU level.

---

## Dashboard 2 — Placement-by-Placement Breakdown

**Business question:** Which sponsored placement types are pulling their weight, and which are burning impression budget?

**Sense AI headline**
> *Hero banner placements show 5x lower CR than the placement-average and contribute the largest single source of opportunity cost across the Adidas portfolio.*

| Placement | Exposure sessions | Clicks | CTR | ATC | ATC rate | Conv. | CR (of clicks) | Revenue | RPME¹ | Frustration² |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|:---:|
| Hero banner (homepage) | 850,000 | 11,900 | **1.40%** 🟠 | 1,071 | **9.0%** 🟠 | 357 | **3.0%** 🔴 | **$39,270** | **$46** 🔴 | 0.42 ⚠️ |
| Search carousel | 620,000 | 24,800 | 4.00% | 3,720 | 15.0% | 1,488 | 6.0% | $163,680 | $264 | 0.18 |
| Category PLP slot | 480,000 | 14,400 | 3.00% | 1,728 | 12.0% | 547 | **3.8%** 🟠 | $60,170 | $125 🟠 | 0.21 |
| PDP cross-sell | 320,000 | 22,400 | 7.00% | 3,136 | 14.0% | 1,254 | 5.6% | $137,940 | $431 | 0.19 |
| Checkout upsell | 95,000 | 5,700 | 6.00% | 1,425 | 25.0% | 798 | **14.0%** 🟢 | $87,780 | **$924** 🟢 | 0.14 |
| Branded landing page | 35,000 | 4,200 | 12.00% | 588 | 14.0% | 134 | **3.2%** 🔴 | $14,740 | $421 | 0.38 ⚠️ |
| **TOTAL / weighted avg** | **2,400,000** | **83,400** | **3.48%** | **11,668** | **14.0%** | **4,578** | **5.49%** | **$503,580** | **$210** | 0.24 |

¹ RPME = Revenue Per Mille Exposures (attributed revenue per 1,000 exposure sessions).
² Contentsquare Frustration Score, 0–1. ⚠️ = >0.35, elevated.

**What to do with this**
- **Hero banner** is the worst placement on every conversion-side metric *and* drives the highest frustration. Audit creative (autoplay video, 3.2s LCP, rage-click hotspots on dismiss "X"). Either retire or move to a CPM-only model and reprice down.
- **Branded landing page** has the highest CTR (12%) but converts at 3.2% — classic "good ad, broken landing experience". Pull Session Replay sample for the 588 ATC-then-bounce sessions.
- **Checkout upsell** is wildly underutilized — 4% of total exposure budget but 17% of revenue. Push for inventory expansion: more SKUs eligible, broader trigger logic.

**Data requirements:** Page-mapping with page groups for Homepage, Search Results, Category PLP, PDP, Cart, Checkout, Order Confirmation; Zoning click-zones per placement slot; segments per placement-exposure built from `click zone` filters; Frustration Score enabled on retail mapping.

---

## Dashboard 3 — Zone-Level Heatmap Comparison

**Business question:** Where on the page does sponsored content actually capture attention, and are we positioning Adidas placements in the strongest real estate?

**Sense AI headline**
> *Above-the-fold sponsored zones outperform below-the-fold by 2.4x on click rate, but PDP cross-sell zones invert this pattern — converting better mid-page than at the top.*

**Engagement Intensity** = (Exposure rate × Click rate × Attractiveness) normalized to 0–100.

### Homepage (Adidas-eligible zones)
```
┌─────────────────────────────────────────────────────┐
│  TOP NAV / SEARCH                                   │
├─────────────────────────────────────────────────────┤
│ ┌─── HERO BANNER (Adidas Originals ZX 500 RM) ───┐ │
│ │ Exposure 92% | CTR 1.4% | Hesitation 8.1s      │ │  ▓▓▓▓░░░░░░  41
│ │ ATF                                             │ │
│ └─────────────────────────────────────────────────┘ │
│ ┌─── Search carousel ───┐ ┌─── Brand spotlight ──┐ │
│ │ Exp 78% | CTR 4.0%    │ │ Exp 64% | CTR 2.8%   │ │  ▓▓▓▓▓▓▓░░░  73 / ▓▓▓▓▓░░░░░  52
│ │ ATF                   │ │ ATF                  │ │
│ └───────────────────────┘ └──────────────────────┘ │
│ ──────────────────  FOLD  ──────────────────       │
│ ┌─── Trending strip ──────────────────────────────┐ │
│ │ Exposure 41% | CTR 0.9%                         │ │  ▓▓░░░░░░░░  19
│ └─────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘
```

### Category PLP (athletic footwear)
```
┌─── Sponsored row 1 (positions 1–4) ───┐
│ Exposure 89% | CTR 3.4% | Att. 0.62   │   ▓▓▓▓▓▓▓░░░  68
└────────────────────────────────────────┘
┌─── Sponsored row 2 (positions 13–16) ─┐
│ Exposure 52% | CTR 2.1% | Att. 0.41   │   ▓▓▓▓░░░░░░  34
└────────────────────────────────────────┘
┌─── Sponsored row 3 (positions 25–28) ─┐
│ Exposure 23% | CTR 1.6% | Att. 0.28   │   ▓▓░░░░░░░░  14
└────────────────────────────────────────┘
```

### PDP (cross-sell modules)
```
┌─── "Often bought with" (above reviews) ──┐
│ Exposure 71% | CTR 5.8% | Att. 0.71      │   ▓▓▓▓▓▓░░░░  62
└───────────────────────────────────────────┘
┌─── "You may also like" (mid-scroll) ──────┐
│ Exposure 84% | CTR 8.2% | Att. 0.83      │   ▓▓▓▓▓▓▓▓▓░  87   ← peak
└───────────────────────────────────────────┘
┌─── "Recently viewed" (footer) ────────────┐
│ Exposure 38% | CTR 2.1% | Att. 0.32      │   ▓▓▓░░░░░░░  22
└───────────────────────────────────────────┘
```

**What to do with this**
- The mid-scroll PDP cross-sell zone is the highest-converting real estate on the entire site — and Adidas currently buys only the "Often bought with" slot above it. Pitch the mid-scroll position as a premium upsell.
- Category PLP positions 25+ are exposure-starved (23% exposure rate). Either reprice those slots down or convert them into dynamic positions that surface for engaged scrollers only.
- Hero banner's 8.1s hesitation time signals confusion, not interest — corroborates the Frustration Score in Dashboard 2.

**Data requirements:** Zoning Analysis enabled on Homepage, Category PLP, and PDP page groups; click-zones defined per placement slot, named consistently with Merchandising catalog product groups for cross-reference.

---

## Dashboard 4 — Top 3 / Bottom 3 Placements by Conversion Rate

**Business question:** Where should the next dollar of sponsored creative effort go, and which placements should we pull?

**Sense AI headline**
> *Checkout upsell delivers 14% CR — the strongest in the portfolio — yet absorbs only 4% of total exposure budget. Reallocation candidate.*

### 🟢 Top 3 (by CR of clicks)

| Rank | Placement | CR | Revenue contribution | Stat. sig.¹ | One-line diagnostic |
|---:|---|---:|---:|:---:|---|
| 1 | Checkout upsell | 14.0% | $87,780 (17%) | ✅ p<0.01 | High-intent context + relevance; SKU-match logic is working. Push for 2x inventory. |
| 2 | Search carousel | 6.0% | $163,680 (32%) | ✅ p<0.01 | Query-aligned creative is the unlock; mobile lift driving growth. |
| 3 | PDP cross-sell | 5.6% | $137,940 (27%) | ✅ p<0.01 | "Often bought with" outperforms "You may also like" in Adidas-only filter; surface as ATF default. |

### 🔴 Bottom 3 (by CR of clicks)

| Rank | Placement | CR | Revenue contribution | Stat. sig. | One-line diagnostic |
|---:|---|---:|---:|:---:|---|
| 1 | Hero banner | 3.0% | $39,270 (8%) | ✅ p<0.01 | High exposure, very low click follow-through; elevated frustration (0.42). Replay cohort: 421 rage-click sessions queued. |
| 2 | Branded landing page | 3.2% | $14,740 (3%) | ⚠️ p=0.04 | Highest CTR (12%) but landing page friction kills conversion — pull replay sample of the 454 click-then-bounce sessions. |
| 3 | Category PLP slot | 3.8% | $60,170 (12%) | ✅ p<0.01 | Exposure rate fine, but ATC rate (12%) underperforms placement average (14%); test SKU-match relevance. |

¹ Two-proportion z-test, control = placement-portfolio average, n = clicks per placement.

**What to do with this**
- Reallocate 30% of Hero banner budget ($12K) to Checkout upsell and Search carousel — projected revenue gain $19K–$28K at current CR.
- Open three Session Replay investigations: Hero banner rage-clicks, Branded landing page bouncers, Category PLP slot non-ATCers. Target: one Replay-driven creative/UX fix per placement within 14 days.
- Hold weekly review for Branded landing page until significance reaches p<0.01 or placement is retired (currently borderline at p=0.04).

**Data requirements:** Conversion goals defined per placement-attributed funnel; segment per click-zone exposure; Session Replay capture enabled; ability to filter replays by click-zone segment (Replay × Segment integration).

---

## Dashboard 5 — Revenue Impact of Underperforming Placements

**Business question:** If we fixed the bottom-quartile placements, how much money is on the table?

**Sense AI headline**
> *Bringing the bottom three placements to portfolio median CR represents $521K in annualized revenue with 95% statistical confidence.*

**Methodology:** Contentsquare Impact Quantification compares each bottom-quartile placement's current conversion behavior against (a) placement-portfolio median CR and (b) top-quartile CR. Lift = projected uplift if placement reached benchmark, holding click volume and AOV constant. CIs derived from click-volume sampling distribution at 95% confidence.

**Placement-by-placement opportunity**

| Placement | Current CR | Current revenue | Lift to median (4.7% CR) | Lift to top-quartile (6.0% CR) |
|---|---:|---:|---:|---:|
| Hero banner | 3.0% | $39,270 | **+$22,253** (CI ±$3,338) | **+$39,270** (CI ±$5,890) |
| Branded landing page | 3.2% | $14,740 | **+$6,930** (CI ±$1,800) | **+$12,936** (CI ±$3,360) |
| Category PLP slot | 3.8% | $60,170 | **+$14,256** (CI ±$2,710) | **+$34,848** (CI ±$6,620) |
| **Portfolio total — monthly** | — | **$114,180** | **+$43,439** (CI ±$5,070) | **+$87,054** (CI ±$10,580) |
| **Annualized** | — | **$1,370,160** | **+$521,268** | **+$1,044,648** |

**Decision matrix**

| Action | Investment | Time-to-value | Expected lift (annualized) | Recommendation |
|---|---|---|---|---|
| Hero banner creative refresh + page-speed fix | ~$45K | 6 weeks | $250K | ✅ Proceed |
| Branded landing page rebuild (mobile-first) | ~$80K | 10 weeks | $90K | 🟡 Hold pending Replay diagnosis |
| Category PLP slot SKU-match retune | ~$15K | 3 weeks | $180K | ✅ Proceed |

**What to do with this**
- Greenlight Hero banner and Category PLP slot work this sprint; combined annualized lift of $430K against $60K investment is a 7x return on optimization spend before any reallocation gains.
- Hold Branded landing page rebuild until Session Replay diagnosis (Dashboard 4) tells us whether the issue is page UX (rebuild needed) or audience-mismatch (cheaper targeting fix).

**Data requirements:** Contentsquare Impact Quantification on retail mapping; placement-level segments; placement-level conversion goals; minimum 4 weeks of stable traffic per placement for statistical reliability.

---

## Dashboard 6 — Brand-Partner Yield & Inventory Report (Retailer-Side)

**Business question:** How is the retailer's commerce media inventory selling, who's the strongest revenue base, and which accounts are at renewal risk?

**Sense AI headline**
> *Two brand partners are flagged for renewal risk this period; combined declining revenue of $42K could be recovered with creative refresh on hero placements.*

### Inventory yield by placement type

| Placement | Fill rate | Avg CPM | Avg sell-through cycle | YoY revenue trend |
|---|---:|---:|---:|---:|
| Hero banner (homepage) | 92% | $48 | 3 days | +6% |
| Search carousel | 87% | $32 | 5 days | +24% |
| Category PLP slot | 81% | $24 | 8 days | +11% |
| PDP cross-sell | 73% | $18 | 11 days | +18% |
| Checkout upsell | 65% | $52 | 14 days | +41% |
| Branded landing page | 100%¹ | flat $18K | n/a | +9% |

¹ Sold as flat-fee sponsorship, not auction-priced.

### Sponsored share of revenue by category

| Category | Sponsored revenue | Organic revenue | Sponsored % |
|---|---:|---:|---:|
| Athletic footwear | $1.84M | $11.3M | **14%** |
| Apparel | $1.21M | $12.4M | 9% |
| Accessories | $620K | $2.2M | **22%** |
| Beauty | $880K | $4.0M | 18% |
| Electronics | $740K | $6.0M | 11% |

### Top 5 brand spenders — Last 30 days

| Rank | Brand | Spend | ROAS (brand-side) | Sponsored revenue (retailer-side) | MoM trend |
|---:|---|---:|---:|---:|---:|
| 1 | Nike | $185,000 | 4.2x | $777,000 | +9% |
| 2 | **Adidas** | **$128,000** | **3.93x** | **$503,580** | **+18%** |
| 3 | Under Armour | $96,000 | 3.1x | $297,600 | -4% |
| 4 | New Balance | $74,000 | 3.6x | $266,400 | +12% |
| 5 | Puma | $58,000 | 2.4x | $139,200 | -22% 🔴 |

### Renewal-risk flags (>20% MoM performance decline)

| Brand | Placement(s) affected | Metric | MoM change | Recommended outreach |
|---|---|---|---:|---|
| Puma | Hero banner, Category PLP | Revenue | -22% | Q3 creative refresh workshop |
| Asics | PDP cross-sell | ATC rate | -23% | SKU-match audit, replay diagnostic |

**What to do with this**
- Schedule renewal conversation with Adidas in next 14 days while ROAS is at 3.93x and trending up — pitch the 30% inventory uplift for Q3.
- Proactive outreach to Puma and Asics with a diagnostic report (use this same dashboard template applied to their brand) before they raise the issue. Avoids passive renewal loss.
- Checkout upsell has the highest CPM ($52) but lowest fill rate (65%) — pricing is right, but supply-side problem. Loop in product/eng to expand trigger logic.

**Data requirements:** Brand-tagged Merchandising catalog with at least the top 50 brand partners; placement-attributed revenue at brand level; ad-server/SSP join with Contentsquare data to bring spend into the same view; baseline period for MoM comparisons.

---

## Dashboard 7 — Audience & Halo Effect Report

**Business question:** Who is sponsored content actually reaching, and is it creating value beyond direct attribution?

**Sense AI headline**
> *Loyalty members convert at 2.1x the rate of first-time visitors when exposed to sponsored Adidas placements — argues for member-priority targeting in the next campaign.*

### Audience composition of Adidas-exposed sessions

| Segment | Share of exposures | Share of revenue | CR (of clicks) | Avg order value |
|---|---:|---:|---:|---:|
| High-intent shoppers (LTV >$200) | 18% | 41% | 9.4% | $134 |
| Loyalty members | 22% | 28% | 7.8% | $118 |
| Lapsed customers (90+ days inactive) | 32% | 22% | 4.2% | $98 |
| First-time visitors | 28% | 9% | 3.7% | $92 |

### Halo effect — campaign window vs control period

| Organic metric (Adidas brand, non-sponsored entry points) | Pre-campaign baseline | During campaign | Δ |
|---|---:|---:|---:|
| Organic Adidas PDP views | 142,000 | 176,400 | **+24%** |
| Organic Adidas brand search queries | 38,200 | 50,000 | **+31%** |
| Organic Adidas add-to-cart (no sponsored click in session) | 8,400 | 9,900 | **+18%** |
| Estimated halo revenue (untracked by direct attribution) | — | **$94,200** | — |

**Effective ROAS including halo: ($503,580 + $94,200) / $128,000 = 4.67x** _(vs reported 3.93x)_

**What to do with this**
- Pitch Adidas the "halo-inclusive ROAS" methodology as a renewal upgrade — moves reported ROAS from 3.93x to 4.67x without changing actual performance.
- Targeting recommendation for next campaign: weight 60% spend toward Loyalty + High-intent segments (combined 40% of exposures, 69% of revenue). Reduce First-time visitor share unless campaign objective is awareness.
- Build a standing "Halo measurement" view per top-10 brand — this is one of the few measurements competitors (Amazon Ads, Walmart Connect) can't deliver well, and it's a differentiator for retention.

**Data requirements:** Loyalty/LTV/recency segments built in Contentsquare from ecommerce-API customer attributes; campaign-window date markers (annotations on retail mapping); ability to compare metric deltas vs a baseline period (Impact module or page-comparison tool); halo methodology documented and reproducible.

---

## Appendix — Instrumentation Prerequisites

Everything the retailer needs configured in Contentsquare to produce the seven dashboards above. Map this checklist against the current project to identify gaps.

### Merchandising
- Product catalog ingested with required fields: `id` (SKU matching ecommerce APIs), `item_group_id` (variants), `title`, `product_type` (hierarchical categories), `link`, `image_link`, `brand`, `price`, `gtin`, `shipping`, `stock`.
- All brand partners tagged in catalog `brand` field — minimum coverage of top 50.
- Product-matching method selected (SKU-in-URL recommended); coverage spot-checked at >85%.

### Page mapping (retail)
- Page groups: Homepage, Search Results, Category PLP, Brand Landing Pages, PDP, Cart, Checkout, Order Confirmation.
- Mapping marked as canonical retail mapping for the project.

### Zoning Analysis
- Click-zones defined per sponsored placement slot, named consistently with placement type (`hero_banner_homepage`, `search_carousel_results`, `plp_slot_row1_pos1-4`, `pdp_crosssell_oftenboughtwith`, etc.).
- Above-the-fold / below-the-fold annotations per zone.

### Goals
- Pageview goals: Reached PDP, Reached Cart, Reached Add to Cart, Reached Order Received.
- Click goals: Click Add to Cart, Click on sponsored placement (one per placement type).

### Segments
- Exposure segment per placement type (filter: zone exposure = X).
- Audience segments: High-intent shoppers (LTV threshold), Loyalty members, Lapsed customers (recency), First-time visitors.
- Brand-exposure segments for top 50 brand partners.

### Ecommerce APIs
- Add to Cart event firing on every ATC interaction with SKU + price + currency.
- Transaction event firing on order completion with full line-item detail and order revenue.
- SKUs in events match SKUs in Merchandising catalog (validation required).

### Frustration Score
- Enabled on retail mapping.
- Per-placement aggregation built from segment × frustration score average.

### Session Replay
- Capture enabled; sampling rate sufficient to populate placement-level cohorts (suggest 100% for sponsored-placement sessions).
- Replay filterable by click-zone segment.

### Impact Quantification
- Available on retail mapping.
- Conversion goal: Reached Order Received (or revenue equivalent).
- Minimum 4 weeks of stable traffic per placement for stat-significant comparisons.

### Sense AI
- Enabled on retail project.
- Custom insight subscriptions: revenue MoM, placement-level CR anomalies, brand-level halo deltas.

### Cross-system joins (not in CSQ but required)
- Ad-server / SSP feed of placement-level spend, joined on placement ID + date.
- Brand partner CRM record for renewal date and account owner.

---

*Showcase document — illustrative figures only. Reproducible against any Contentsquare DXA + Merchandising + Zoning deployment with the prerequisites above.*
