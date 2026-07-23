# CTR Opportunity Scoring for Search Content
### A Rule-Based Approach for Identifying High-Visibility, Low-CTR Pages

**Author:** Manaswini Reddy  
**Track:** FlyRank Machine Learning Internship  
**Lane:** CTR / Engagement Opportunity Scoring  
**Repository:** (Add your GitHub repo URL here)

---

# Abstract

This study develops a rule-based content opportunity scoring system for identifying webpages that receive high search visibility but comparatively low click-through rates (CTR). Using anonymized search performance data from the FlyRank ML Internship warehouse, pages were aggregated at the monthly level and analyzed using Google Search Console performance metrics. A transparent baseline scoring rule combining impressions, CTR, and average search position was developed to prioritize pages most likely to benefit from metadata or content improvements. The resulting ranked review queue demonstrates how simple, explainable decision rules can support content optimization while avoiding data leakage and maintaining reproducible analysis. This work serves as a practical decision-support system rather than a predictive model.

---

# 1. Introduction

Search teams often manage thousands of webpages simultaneously, making manual identification of optimization opportunities difficult. Pages with high visibility but unusually low CTR frequently represent valuable opportunities because even small improvements may generate meaningful increases in organic traffic.

The objective of this project is to develop a transparent rule-based scoring workflow that automatically ranks pages requiring review. Rather than predicting future search performance, the workflow prioritizes existing content using interpretable search metrics and clearly defined business rules.

The final output is a ranked review queue with reason codes and recommended actions that can assist content editors in deciding which pages to review first.

# 2. Data

## Dataset

This project uses the anonymized FlyRank ML Internship Warehouse dataset available through Hugging Face. Analysis was performed directly on the warehouse using DuckDB without downloading the complete dataset.

The primary table used is:

- `fact_content_daily_performance`

The table contains daily search performance statistics for anonymized webpages across multiple clients.

---

## Time Window

Development was performed using **March 2026** (`month = '2026-03'`).

The final month (June 2026) was intentionally excluded because the internship documentation recommends treating it as a sealed evaluation period rather than using it during feature development.

---

## Unit of Analysis

The daily table was aggregated into one row per:

**Client × Content Page × Month**

Each row therefore represents the monthly search performance of one webpage for one client.

---

## Features Used

Only information available at the decision moment was used.

The baseline scoring workflow uses:

- Google Search impressions
- Google Search clicks
- Click-through rate (CTR)
- Average search position

These features are directly observable from historical search performance and require no future information.

---

## Excluded Fields

Several fields were deliberately excluded to avoid leakage or unnecessary complexity.

Excluded examples include:

- Future performance information
- Product-generated labels
- Trend or outcome indicators
- Client identifiers as predictive features

Client and content IDs were used only for grouping and aggregation, never as model inputs.

---

## Data Safety

The dataset contains anonymized identifiers only.

No client names, domains, URLs, search queries, or private business information are included in this report.

All results are presented only as aggregate statistics and decision-support analysis.

# 3. Methodology

## Research Question

Can search performance metrics identify pages that are highly visible but receive fewer clicks than expected, allowing editors to prioritize content for CTR improvement?

---

## Baseline Approach

A transparent rule-based scoring system was developed before considering any machine learning model.

Each page receives an action score using only historical search metrics available at the decision time.

The score prioritizes pages that have:

- High search impressions
- Low click-through rate (CTR)
- Strong average search position

These characteristics indicate pages that already receive substantial visibility but may underperform in attracting clicks.

---

## Signal Validation

Before designing the scoring rule, two assumptions were validated using warehouse data.

### Signal 1 — CTR versus Position

Pages were grouped into position buckets.

Observed result:

- Higher-ranked pages generally achieved higher CTR.
- Pages with good rankings but unusually low CTR represent potential optimization opportunities.

Verdict: **CONFIRMED**

---

### Signal 2 — Search Volume

Pages were grouped by monthly impressions.

Observed result:

- High-impression pages contribute the largest share of search traffic.
- Improving CTR on these pages is likely to produce greater overall impact than optimizing low-traffic pages.

Verdict: **CONFIRMED**

---

## Scoring Rule

The baseline action score combines search visibility with CTR deficiency.

Higher scores are assigned to pages that satisfy the following characteristics:

- Large number of impressions
- Low click-through rate
- Good search position

Each prioritized page receives:

- Action Score
- Reason Code
- Recommended Action

Example:

Reason Code:
`LOW_CTR_VISIBLE_PAGE`

Recommended Action:
`Review CTR & Content`

---

## Leakage Prevention

Only information available before making the recommendation was used.

The workflow deliberately excludes:

- Future observations
- Product-generated labels
- Outcome variables
- Trend-derived fields

This ensures that the baseline score reflects a realistic decision-support workflow rather than benefiting from future information.

---

## Validation Strategy

The baseline does not predict future outcomes.

Instead, it ranks pages according to their optimization priority.

The ranked output is then manually reviewed to assess whether the highest-scoring pages represent reasonable candidates for CTR improvement.

# 4. Results

## Dataset Summary

The analysis was performed using the FlyRank Internship Warehouse dataset for **March 2026**.

Summary of the working dataset:

| Metric | Value |
|---------|-------|
| Monthly page rows | 176,738 |
| Clients | 55 |
| Content pages | 331,437 |
| Date range | 2026-03-01 to 2026-03-31 |

---

## Signal Validation Results

Two assumptions behind the baseline scoring rule were validated before constructing the ranking.

### Signal 1 — CTR vs Average Position

Pages appearing in better search positions generally achieved higher click-through rates.

This supports prioritizing pages that rank well but receive unusually few clicks.

**Verdict:** CONFIRMED

*(Insert your CTR vs Position bucket table screenshot here.)*

---

### Signal 2 — Search Volume

Pages with higher search impressions represented the largest optimization opportunity.

Although CTR varies across traffic levels, improving CTR on high-impression pages has the greatest potential impact.

**Verdict:** CONFIRMED

*(Insert your Search Volume bucket table screenshot here.)*

---

## Baseline Ranking

The scoring workflow generated a ranked review queue containing pages with:

- High impressions
- Good search visibility
- Low click-through rate

Each page received:

- Action Score
- Reason Code
- Recommended Action

Example reason code:

**LOW_CTR_VISIBLE_PAGE**

Recommended action:

**Review CTR & Content**

*(Insert screenshot of the Top-20 ranked pages here.)*

---

## Observations

The highest-ranked pages consistently showed the same pattern:

- Strong visibility in Google Search
- Large search impression counts
- Lower-than-expected CTR

These pages represent reasonable candidates for metadata review, title optimization, and content improvements.

---

## Limitations

This workflow is intended as a decision-support baseline rather than a predictive model.

The scoring rule does not estimate future CTR improvements and was not evaluated using production outcomes.

Instead, it provides an explainable ranking that can guide manual review by content editors.

# 5. Discussion

The baseline scoring workflow demonstrates that simple, transparent rules can identify content pages that deserve manual review without requiring a machine learning model.

The signal validation showed that pages ranking in stronger search positions generally achieve higher click-through rates, while high-impression pages provide the largest optimization opportunity. These observations support using search visibility and CTR together when prioritizing content.

The rule-based approach is intentionally explainable. Every recommendation includes both a reason code and an action label, allowing editors to understand why a page was selected.

One limitation is that this workflow does not predict future performance or estimate the impact of content changes. It is designed as an evidence-based ranking system for decision support rather than an automated optimization engine.

Future work could extend this baseline by training supervised machine learning models to predict CTR improvement potential while maintaining strict leakage controls and time-aware validation.

---

# 6. Conclusion

This project built a baseline content prioritization workflow using the FlyRank Internship Warehouse dataset.

Instead of relying on complex machine learning, the workflow combines search impressions, click-through rate, and search position into an interpretable action score that identifies pages with high optimization potential.

The resulting ranked queue provides explainable recommendations that content editors can use as a starting point for manual review.

The project demonstrates how transparent analytics can support content optimization while establishing a strong baseline for future machine learning approaches.

---

# 7. Reproducibility

Repository:
> (Insert your GitHub repository URL)

Main notebook:

- work/notebooks/w03_data_contract.ipynb
- work/notebooks/w04_baseline_score.ipynb

Environment

- Python 3
- DuckDB
- Pandas
- Hugging Face Datasets
- Google Colab

The analysis can be reproduced by requesting access to the FlyRank Internship Warehouse dataset, creating a Hugging Face Read Token, and executing the notebooks from top to bottom.

---

# 8. Acknowledgments

This project was completed as part of the **FlyRank Machine Learning Internship**.

The analysis uses the **FlyRank Internship Warehouse Dataset** provided for educational and research purposes.

Data source:
https://flyrank.ai

Special thanks to the FlyRank mentorship program for providing the problem statements, warehouse dataset, and learning materials that guided this project.
