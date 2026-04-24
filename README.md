# Online Retail — Customer Retention Analysis

A product analytics case study examining why customers return after their first purchase, how quickly they return, and what distinguishes one-time buyers from repeat buyers on a UK-based online retail platform.

---

## The Business Question

Most e-commerce businesses assume their biggest problem is retention — getting customers to come back. This analysis tests that assumption directly and finds something more interesting: **this platform's retention is already exceptional**. The real opportunity lies elsewhere.

---

## Dataset

**Source:** [Online Retail II — UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)

**Period:** December 2009 – December 2011 (24 months)

**Raw size:** 1,067,371 rows across 8 columns

**After cleaning:** ~800,000+ rows, 5,881 unique trackable customers

**Columns used:**

| Column | What it represents in product terms |
|---|---|
| Invoice | A completed purchase session (one checkout) |
| StockCode | Item-level interaction |
| Description | Product metadata |
| Quantity | Engagement intensity (negative = return) |
| InvoiceDate | Event timestamp — the backbone of all analysis |
| Price | Value generated per item |
| Customer ID | User identity — required for retention tracking |
| Country | Geographic segmentation |

---

## Project Structure

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

## Methodology

### Data Cleaning Decisions

**Customer ID recovery:** Rather than immediately dropping rows with missing Customer IDs, we first attempted recovery using a two-column match — Invoice number AND InvoiceDate. If a row with a missing Customer ID shared both columns with a row containing a valid Customer ID, the ID was filled in. Only rows with no match on either column were flagged as truly anonymous and dropped.

**Exclusions:**
- Cancellation invoices (Invoice starting with "C")
- Negative quantity rows (returns) — retained separately for H6 analysis
- Rows with unrecoverable Customer IDs

### Focus Metric

> **The percentage of activated customers who make a second purchase within 30 days of their first purchase.**

- **Activation** = at least one invoice with positive quantities and a valid Customer ID
- **Second purchase** = a different Invoice number with at least one positive quantity line
- **Denominator** = all activated customers, regardless of whether they returned

### Guardrail Metric

> **The percentage of second-purchasers who go on to make a third purchase within 60 days.**

Ensures that optimising for 30-day second purchases does not manufacture artificial repeat behaviour at the expense of genuine long-term loyalty.

### The 7 Hypotheses

| # | Hypothesis | Result |
|---|---|---|
| 1 | Most customers do not return after their first purchase | Rejected |
| 2 | Customers who return, return quickly (within 30 days) | Rejected |
| 3 | The largest drop-off happens after the first purchase | Confirmed |
| 4 | One-time buyers behave differently from repeat buyers in session 1 | Confirmed |
| 5 | Second purchasers are significantly more likely to keep buying | Rejected |
| 6 | Returns and cancellations correlate with lower retention | Rejected |
| 7 | Retention varies significantly by country | Rejected |

---

## Key Findings

**This is not a retention problem — it is an acquisition targeting opportunity.**

72.4% of customers are repeat buyers, far exceeding the 20–40% industry benchmark for online retail. The customer base is dominated by wholesale buyers and resellers who purchase in volume, make returns as part of their normal cycle, and are the most loyal segment in the dataset.

**The five most important findings:**

1. **Retention is exceptional but concentrated.** 72.4% repeat rate signals a wholesale-dominated customer base, not a casual consumer one. Acquisition should target more customers who look like the existing loyal base.

2. **Two customer types are hiding in the data.** 32.7% of returning customers come back within 30 days (likely resellers) and 35.4% take 90+ days (likely seasonal buyers). One re-engagement strategy will not serve both groups.

3. **First-session behaviour predicts loyalty.** Repeat buyers spent 32% more, bought 26% more items, and explored 19% more unique products in their very first session. This is a measurable activation threshold that can be acted on in real time.

4. **Returners are the most loyal customers.** Customers with 4+ returns retained at 96.1% — the opposite of what was expected. Returns are a signal of wholesale engagement, not dissatisfaction.

5. **The data is 91% UK-based.** Geographic expansion cannot be meaningfully informed by this dataset at its current scale.

---

## Recommendations

| Priority | Action |
|---|---|
| 1 | Reframe the business problem — this is an acquisition problem, not a retention problem |
| 2 | Build a first-session scoring system — flag customers spending £307+ or buying 3+ product categories |
| 3 | Segment re-engagement by return timing — 30-day outreach for fast returners, 90-day for slow |
| 4 | Investigate returns by product and location — operational insight, not a churn problem |
| 5 | Deepen UK market before international expansion |

---

## Tools Used

- **Python 3** — core analysis
- **pandas** — data manipulation
- **numpy** — numerical operations
- **matplotlib / seaborn** — visualisation
- **Jupyter Notebook** — analysis environment

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/JoshuaF/product-analytics-user-retention.git

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Download the dataset
# Get Online Retail II from UCI ML Repository:
# https://archive.ics.uci.edu/ml/datasets/Online+Retail+II
# Place the CSV in the data/ folder

# 4. Launch Jupyter
jupyter notebook

# 5. Open and run notebooks/retention_analysis.ipynb
# Run cells top to bottom in order
```

---

## What I Learned

This project taught me that the most valuable findings often come from rejected hypotheses. The assumption going in was that this platform had a retention problem. The data showed the opposite — and understanding *why* the opposite was true (wholesale buyers, return cycles, first-session signals) produced more actionable insights than confirming the original hypothesis would have.

The analysis also reinforced the danger of aggregate metrics: a 27.6% one-time buyer rate looks concerning until you segment it and realise the 72.4% who return are exceptional — and the 27.6% represent an acquisition opportunity, not a product failure.

---

## Author

**Joshua Paul Lasisi**
Product Analyst | Data Analyst
[LinkedIn](https://linkedin.com/in/joshuapaul-lasisi) | [GitHub](https://github.com/JoshuaF) | [Portfolio](https://sky-knight-aae.notion.site/Joshua-Paul-lasisi-Data-Scientist-f2d9b50cd28240c49d267cc4dec5b73c)
