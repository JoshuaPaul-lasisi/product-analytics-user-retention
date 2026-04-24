# Why Most Customers Buy Once and Leave — and What Drives the 30-Day Return Rate

**Project Type:** Cohort Retention Analysis | Product Analytics  
**Dataset:** Online Retail II — UCI Machine Learning Repository  
**Analyst:** Joshua Paul Lasisi  
**Tools:** Python · Pandas · Matplotlib · Seaborn · Jupyter Notebook

---

## Business Context

This dataset belongs to a UK-based online retail platform selling physical goods — primarily home décor, gifts, and novelty items — across 43 countries from December 2009 to December 2011. The platform operates on a transactional model where revenue is generated per purchase session, not per subscription.

For a platform of this type, the health of the business is visible not in acquisition numbers but in whether customers come back. A customer who buys once and disappears contributes far less long-term value than one who returns repeatedly, even at lower order sizes.

**This analysis answers five core questions:**
1. How many users return after their first purchase — and is retention actually a problem?
2. How quickly do returning customers come back?
3. Where is the largest customer drop-off in the purchase journey?
4. What distinguishes repeat buyers from one-time buyers — can we predict loyalty early?
5. Do operational frictions like returns and cancellations hurt long-term retention?

---

## Focus Metric

**30-Day Second Purchase Rate** — the percentage of activated customers who make a second purchase within 30 days of their first.

A customer is *activated* when they complete at least one invoice with positive quantities and a valid Customer ID. Returns-only customers are not counted as activated. The denominator is all activated customers, regardless of whether they returned.

This metric was chosen because it is specific, directly measurable from available data, and actionable — a low rate signals where to direct retention effort.

**Supporting Metrics:**
- Overall second-purchase conversion rate (without a 30-day time constraint)
- Median time between first and second purchase
- Average purchases per customer per 30 days

**Guardrail Metric:** Percentage of second-purchasers who go on to make a third purchase within 60 days. This guards against manufacturing second purchases artificially — through discounts or urgency tactics — without generating genuine loyalty.

---

## Dataset

**Source:** [Online Retail II — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii)

| Column | Product Interpretation |
|---|---|
| Invoice | A completed purchase session (one checkout) |
| StockCode | Item-level interaction |
| Description | Product metadata |
| Quantity | Engagement intensity (negative = return) |
| InvoiceDate | Event timestamp — backbone of cohort analysis |
| Price | Value generated per item |
| Customer ID | User identity — required for retention tracking |
| Country | Geographic segment |

**Scale:** 1,067,371 rows · 5,942 unique customers · 53,628 unique invoices · 43 countries · 738-day span

---

## Data Quality

| Issue | Decision | Implication |
|---|---|---|
| 242,000 rows missing Customer ID | Recovery attempted first using Invoice + InvoiceDate matching. Rows with no match on both columns were flagged and dropped. | Rows where the same invoice appeared elsewhere with a Customer ID were recovered. Truly anonymous transactions were excluded — they cannot be attributed to any user. |
| 22,950 negative quantities | Removed from purchase analysis but retained separately for H6 (returns and retention) | These are returns and cancellations — the opposite of value delivery in purchase terms |
| Invoices starting with "C" | Removed as cancellations | Same logic as negative quantities |
| Missing descriptions | Low priority — description is metadata, not identity | Does not affect customer-level analysis |

The volume of missing Customer IDs (22.7% of rows) and returns (21.5% of rows) at this scale indicates a systemic data entry issue, likely exacerbated by operating across 43 countries without automated recording.

---

## Hypotheses and Findings

### H1 — Most customers do not return after their first purchase
**Result: REJECTED**

72.4% of customers made repeat purchases — well above the 20–40% industry benchmark for online retail. This exceptional rate signals that the customer base is dominated by wholesale buyers and resellers, not casual consumers. The business does not have a retention problem. It has an acquisition opportunity: focus on attracting more customers who resemble the existing loyal base. The 27.6% who never return represent the true leakage point — understanding what separates them from the 72.4% who stay is more valuable than general retention campaigns.

---

### H2 — Returning customers return quickly (within 30 days)
**Result: REJECTED**

The median return time was 55 days, outside the 30-day focus metric window. However, the distribution reveals two distinct patterns: 32.7% return within 30 days and 35.4% take 90+ days, with only 20.1% in the moderate middle. The mean of 97 days versus median of 55 confirms that a small group of very slow returners skews the average significantly — this is precisely why median was chosen over mean. The bimodal pattern suggests two customer segments behaving differently: fast-cycle resellers restocking regularly, and slow-cycle gift buyers returning seasonally. One-size-fits-all retention timing will under-serve both groups. Segmented engagement — immediate re-engagement for fast returners, longer nurture cycles for seasonal buyers — would better match actual behavior.

---

### H3 — The largest drop-off happens immediately after the first purchase
**Result: CONFIRMED**

| Transition | Drop-off |
|---|---|
| Purchase 1 → 2 | 27.6% |
| Purchase 2 → 3 | 22.2% |
| Purchase 3 → 4 | 20.0% |
| Purchase 4 → 5 | 18.3% |

The first-to-second purchase conversion is the steepest drop in the journey — but critically, the drop-off rate declines steadily with each subsequent step, stabilizing as customers progress. This is a healthy funnel shape. Customers become progressively stickier the longer they stay. The business should concentrate retention effort on the 1→2 window, while recognizing that the funnel naturally improves beyond that point.

---

### H4 — One-time buyers and repeat buyers behave differently in their first session
**Result: CONFIRMED**

| First Session Metric | One-Time Buyers | Repeat Buyers |
|---|---|---|
| Median items bought | 132 | 166 (+26%) |
| Median unique products | 16 | 19 (+19%) |
| Median revenue | £231.92 | £307.44 (+32%) |

Repeat buyers spent 32% more, bought 26% more items, and explored 19% more product variety in their very first session — before any indication they would return. First-session behavior is a leading indicator of long-term loyalty. This is the product analytics equivalent of Facebook's "7 friends in 10 days." Customers who spend above £307 or explore 3+ unique product categories in session 1 are high-retention candidates and should be identified and enrolled in loyalty or wholesale programmes immediately after first purchase.

---

### H5 — Second purchasers are significantly more likely to keep buying
**Result: REJECTED**

Drop-off after first purchase: 27.6%. Drop-off after second purchase: 22.2%. Ratio: 1.24× — well below the 2.0× threshold for significance. Conversion improves from 72.4% to 77.8% after the second purchase, but the change is gradual rather than a sharp loyalty cliff. There is no single purchase number that unlocks retention. This reinforces the finding from H1: since most customers are already returning (72.4%), the greater leverage is in activating the 27.6% who never return. For customers who do return, continuous engagement programs across all purchase stages will serve better than concentrating effort on the second purchase alone.

---

### H6 — Returns and cancellations correlate with lower retention
**Result: REJECTED**

| Segment | Retention Rate |
|---|---|
| Non-returners | 58.3% |
| Returners | 91.2% |
| 1 return | 85.7% |
| 2 returns | 86.4% |
| 3 returns | 91.0% |
| 4+ returns | 96.1% |

The hypothesis was rejected in both directions — returners retain dramatically better than non-returners, and retention increases as return volume grows. This is the most counterintuitive finding in the analysis, and also the most informative. High-return customers are wholesale buyers and resellers who return unsold inventory as part of their normal purchasing cycle. They are the most engaged, highest-value segment in the dataset. Non-returners at 58.3% are likely casual individual consumers who never engage deeply enough to bother returning. Returns are not a signal of dissatisfaction — they are a behavioral marker of the most loyal customer type. The business should treat return behavior as a positive identifier, not a problem metric.

---

### H7 — Retention varies significantly by country
**Result: REJECTED**

Only three countries had 50+ customers — the minimum for reliable analysis: UK (5,353), Germany (106), France (95). The retention range across these three was 7.6 percentage points, well below the 20pp significance threshold. More importantly, all three are Western European markets, so this narrow band likely reflects a regional baseline rather than meaningful geographic variation. The headline finding is the concentration itself: 91% of trackable customers are from the UK. The business has deep domestic penetration and a thin international presence. Geographic retention strategy cannot be meaningfully designed from this data until target markets develop sufficient customer volumes. Germany and France are the logical starting points given their existing footprint.

---

## Key Takeaways

1. **This is not a retention-challenged business.** 72.4% repeat purchase rate is exceptional. The priority is not fixing retention — it's attracting more customers who look like the ones already staying.

2. **First-session behavior predicts long-term loyalty.** Customers who spend above £307 or explore 3+ unique product categories in session 1 are significantly more likely to return. This is an actionable early signal.

3. **The 1→2 conversion window is the right focus.** The largest funnel drop-off happens after the first purchase. Everything else improves gradually on its own.

4. **The customer base has two distinct segments.** Fast returners (resellers, ~33%) and slow returners (seasonal buyers, ~35%) require different engagement timing. Unified retention campaigns will miss both.

5. **Returns are a feature, not a bug.** Customers with the most returns are the most loyal. Return behavior should be treated as a high-value customer signal, not reduced.

---

## Repository Structure

```
product-analytics-user-retention/
│
├── data/
│   ├── processed
│   │    └── cleaned_retail.csv          # Cleaned dataset after eda
│   ├── raw
│       └── online_retail_II.csv          # Source dataset (not included — see link above)
│
├── notebooks/
│   └── retention_analysis.ipynb      # Full analysis — hypotheses → findings
│   └── retention_eda.ipynb      # Full eda - cleaning + exploration
│
├── outputs/
│   ├── hypothesis_1_repeat_buyers.png
│   ├── hypothesis_2_return_speed.png
│   ├── hypothesis_3_dropoff.png
│   ├── hypothesis_4_buyer_behavior.png
│   ├── hypothesis_5_second_purchase_loyalty.png
│   ├── hypothesis_6_returns_retention.png
│   └── hypothesis_7_country_retention.png
│
├── .gitattributes
├── analysis-plan.md                  # Full project note — framing, metrics, hypotheses
├── findings_document.md                  # Full project findings compilation post-hypotheses
├── Online Retail Retention Analysis.pdf                  # Full pre-analysis workbook — framing, metrics, hypotheses
└── README.md
```

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/[your-username]/product-analytics-user-retention.git
cd product-analytics-user-retention

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Download the dataset
# https://archive.ics.uci.edu/dataset/502/online+retail+ii
# Place online_retail_II.csv in the /data folder

# 4. Open and run the notebook
jupyter notebook notebooks/retention_analysis.ipynb
```

Run all cells top to bottom. Charts save automatically to `/outputs`.

---

## About This Analysis

This project was built as part of a product analytics portfolio focusing on user retention, cohort analysis, and product-led growth metrics. The analysis methodology follows the product analytics framework: define the product, identify the core value action, set a focus metric, form testable hypotheses, and let the data confirm or challenge them — rather than mining for conclusions.

---

*Dataset: Daqing Chen, Sai Liang Sain, and Kun Guo, Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining, Journal of Database Marketing and Customer Strategy Management, Vol. 19, No. 3, pp. 197â€"208, 2012 (Published online before print: 27 August 2012. doi: 10.1057/dbm.2012.17)*
