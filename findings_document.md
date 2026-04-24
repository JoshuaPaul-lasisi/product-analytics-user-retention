# Online Retail Retention Analysis — Findings
**Dataset:** Online Retail II (UCI Machine Learning Repository)
**Analyst:** Joshua Paul Lasisi
**Period Covered:** December 2009 – December 2011
**Customers Analysed:** 5,881 unique registered customers

---

## Executive Summary

This analysis set out to understand whether and how quickly customers return after their first purchase on an online retail platform, and what distinguishes one-time buyers from repeat buyers. Across seven hypotheses, the data consistently pointed to one central finding: **this is not a retention problem — it is an acquisition targeting opportunity.**

The platform retains 72.4% of its customers as repeat buyers, far exceeding the 20–40% industry benchmark for online retail. The customer base is dominated by wholesale buyers and resellers who purchase in volume, return unsold goods as part of their normal cycle, and remain the most loyal segment in the dataset. The 27.6% who leave after one purchase are the real opportunity — and the data shows exactly what distinguishes them from those who stay: lower spend, fewer items, and less product variety in their very first session.

The five priority actions this analysis recommends are:

1. Shift acquisition targeting toward wholesale and reseller profiles
2. Build a real-time first-session scoring system to identify high-retention customers immediately
3. Segment re-engagement campaigns by return timing — fast returners need 30-day outreach, slow returners need 90-day nurture cycles
4. Investigate what is being returned and from where — returns are a loyalty signal, not a churn signal
5. Deepen the UK market before expanding geographically — 91% of trackable customers are UK-based and the data cannot yet support international strategy

---

## Findings by Hypothesis

### Hypothesis 1 — Most customers are repeat buyers (REJECTED as stated, opposite confirmed)

**What we found:**
72.4% of our total customer base are repeat buyers — nearly 3× the industry benchmark of 20–40% for online retail. Only 27.6% are one-time buyers.

**What this means:**
Retention is not our main issue. The business is already delivering enough value to bring the majority of customers back. This exceptional retention rate tells us we are not dealing with casual browsers — our customer base is dominated by wholesale buyers, resellers, and highly loyal repeat purchasers who return consistently.

**What the business should do:**
The focus should shift from improving retention to improving activation — converting more first-time visitors into the kind of buyer who stays. Since we know 72.4% of our customers return, the question becomes: how do we attract more people who look like them? Acquisition targeting should be oriented toward wholesale and reseller profiles rather than general consumers.

---

### Hypothesis 2 — Customers return in 55 days, not within 30 (REJECTED)

**What we found:**
The median time between first and second purchase is 55 days. However, the distribution reveals a more interesting pattern: 32.7% of returning customers come back within 30 days, while 35.4% take over 90 days. More than 50% of returning customers return within the first 2 months.

**What this means:**
The 55-day median is the average of two fundamentally different customer behaviours — not a single moderate segment. We appear to be dealing with at least two distinct customer types: fast returners who restock quickly (likely resellers), and slow returners who come back seasonally or quarterly (likely gift buyers or occasional wholesale customers). The mean of 97 days versus the median of 55 days confirms this — a small group of very slow returners is pulling the average up significantly.

**What the business should do:**
Marketing and re-engagement campaigns cannot use a single timing strategy. Fast returners need outreach within 30 days of their first purchase. Slow returners need a longer nurture cycle of 60–90 days. These two segments likely respond to completely different messaging — resellers care about stock availability and volume pricing, while seasonal buyers care about product range and occasions. Segmentation is required before any re-engagement programme is built.

---

### Hypothesis 3 — Largest drop-off confirmed at Purchase 1 → 2 (CONFIRMED)

**What we found:**
The steepest customer loss occurs between the first and second purchase at 27.6%. Drop-off rates then decline steadily: 22.2% at 2→3, 20.0% at 3→4, continuing to fall to 13.3% by 8→9. The funnel stabilises progressively with each purchase step.

**What this means:**
The first-to-second purchase conversion is the highest-priority window — but the overall funnel is healthy. Customers get meaningfully stickier with each purchase. This is the expected shape of a well-functioning retention system, not a crisis. The declining drop-off pattern, combined with the insight from Hypothesis 2, suggests we are delivering more than one kind of value — the fast-returning reseller segment and the slow-returning seasonal segment are both staying, just on different timelines.

**What the business should do:**
Focus retention investment on the 1→2 conversion window. This is where the most customers are lost and where intervention has the highest potential return. Beyond that window, the funnel largely takes care of itself. A deeper investigation into what the 27.6% who leave after purchase 1 did differently from those who stayed — building on the insight from Hypothesis 4 — is the logical next step.

---

### Hypothesis 4 — First session behaviour predicts loyalty (CONFIRMED)

**What we found:**
Repeat buyers behaved measurably differently from one-time buyers in their very first session — before we had any way of knowing they would return. Repeat buyers bought 26% more items (median 166 vs 132), explored 19% more unique products (19 vs 16), and generated 32% more revenue (£307 vs £232) in session one.

**What this means:**
First-session behaviour is a leading indicator of long-term loyalty. Single-item buyers and low-variety buyers rarely return — and this makes sense because the customers who buy more items and more variety in session one are the wholesale and reseller types who constitute our loyal 72.4%. They arrive knowing what they want, buy broadly, and come back. One-time buyers arrive, make a small exploratory purchase, and do not find a compelling reason to return.

**What the business should do:**
The business now has an early signal it can act on in real time. Customers who spend above £307 or purchase 3+ unique product categories in their first session should be immediately identified and enrolled in loyalty or wholesale programmes. This is the business's activation threshold — the equivalent of Facebook's "7 friends in 10 days." Building an automated first-session scoring system that flags high-retention candidates for immediate outreach would convert this insight into measurable business value.

---

### Hypothesis 5 — Second purchase does not dramatically change loyalty odds (REJECTED)

**What we found:**
The drop-off ratio between the first-to-second and second-to-third purchase transitions was only 1.24× — well below our 2.0× threshold for significance. Conversion rates improve modestly from 72.4% to 77.8% after the second purchase, but the improvement is gradual rather than a sharp inflection.

**What this means:**
There is no single magic purchase number that unlocks loyalty in this customer base. Retention builds incrementally across every transaction. This finding reinforces Hypothesis 1 — since the majority of customers already return, the more profitable focus is on activation rather than on engineering a loyalty cliff at purchase two. The second purchase matters, but it is not dramatically more powerful than the third or fourth.

**What the business should do:**
Rather than concentrating retention effort on the second purchase specifically, the business should invest in programmes that reward continuous purchasing across all stages — volume discounts, reorder reminders, and account management for wholesale customers. The goal is to keep the funnel moving steadily, not to find a single conversion point to optimise.

---

### Hypothesis 6 — Returners retain significantly better than non-returners (REJECTED as stated, opposite confirmed)

**What we found:**
Customers with returns or cancellations retained at 91.2% — compared to 58.3% for customers with no returns. The relationship strengthens with volume: customers with 4+ returns retained at 96.1%. Non-returners are the lower-retention group.

**What this means:**
The opposite of our hypothesis is true — and the explanation is logical once you understand the customer base. It is the repeat buyers who can and do cancel or return goods multiple times. These are wholesale customers and resellers who order in volume, return what does not sell, and come back to reorder. They are the most engaged, highest-value customers in the dataset — and their return behaviour is part of their purchasing cycle, not a sign of dissatisfaction. The lower-retention non-returners are more likely to be one-time casual buyers who never engage deeply enough to even bother returning.

**What the business should do:**
Returns should not be treated as a problem to reduce. They are a behavioural signal of the most loyal customer segment. Two further investigations are recommended: first, identify what products are being returned and from which locations — this operational insight could improve inventory management. Second, use return behaviour as a positive signal when identifying high-value customers for wholesale programmes and account management. A customer with frequent returns is more valuable, not less.

---

### Hypothesis 7 — Country variation is not measurable with current data (REJECTED)

**What we found:**
Only 3 countries had 50 or more customers: United Kingdom (5,353), Germany (106), and France (95). The retention range across these three countries was 7.6 percentage points — below our 20pp significance threshold. 38 countries were excluded due to insufficient sample sizes.

**What this means:**
The more important finding is not the 7.6pp range — it is the extreme geographic concentration of the data. 91% of trackable customers are from the UK. The "43 countries" in the dataset is technically accurate but misleading: most represent very small footprints, not real market presence. Furthermore, all three comparable countries are in Western Europe, which means the small variation we did observe may simply reflect a continental baseline rather than meaningful geographic differences. A transcontinental comparison — including markets in Asia, North America, or Africa — might show a more significant range, but the data does not yet support it.

**What the business should do:**
Geographic expansion strategy cannot be meaningfully informed by this dataset until customer volumes in target international markets grow to statistically reliable levels. The immediate priority should be deepening the UK market — where the data is rich and the customer base is proven — before committing resources to international growth. Germany and France are the logical first international targets given their existing footprints, but neither has sufficient volume yet for reliable strategic decisions.

---

## Summary of Findings and Recommendations

| Hypothesis | Result | Key Insight |
|---|---|---|
| H1: Most customers are one-time buyers | Rejected | 72.4% are repeat buyers — exceptional retention |
| H2: Returners come back within 30 days | Rejected | Bimodal pattern — two distinct customer segments |
| H3: Largest drop-off after purchase 1 | Confirmed | Healthy declining funnel — priority is 1→2 conversion |
| H4: First session behaviour differs | Confirmed | First session is a leading indicator of loyalty |
| H5: Second purchase drives loyalty sharply | Rejected | Loyalty builds gradually — no single inflection point |
| H6: Returns correlate with lower retention | Rejected | Returners are the most loyal segment — opposite is true |
| H7: Retention varies by country | Rejected | Data is 91% UK — geographic analysis not yet viable |

### Priority Recommendations

1. **Reframe the business problem.** This is not a retention problem. It is an acquisition targeting problem. The product works — bring in more people who resemble the existing loyal base.

2. **Build a first-session scoring system.** Flag customers who spend above £307 or explore 3+ unique product categories in session one. Enrol them in loyalty or wholesale programmes immediately.

3. **Segment re-engagement by return timing.** Fast returners (0–30 days) need immediate outreach. Slow returners (90+ days) need a longer nurture cycle. One campaign strategy will not serve both groups.

4. **Investigate returns by product and location.** Returns are not a churn signal — they are a loyalty signal. But understanding what is returned and from where will improve inventory management and customer experience simultaneously.

5. **Deepen UK before expanding internationally.** 91% of the trackable customer base is UK-based. Build retention and acquisition infrastructure domestically before committing to geographic expansion.

---

## Limitations

- Guest purchases (rows without Customer IDs that could not be recovered via Invoice matching) were excluded from the analysis, meaning a portion of actual transaction volume is not captured in these findings.
- The dataset ends in December 2011. Customer behaviour and market conditions may have changed significantly since then.
- Returns analysis relied on the assumption that all negative-quantity rows represent legitimate returns, not data entry errors.
- Country-level analysis was limited to 3 countries with sufficient sample sizes. International findings should be treated as directional only.
