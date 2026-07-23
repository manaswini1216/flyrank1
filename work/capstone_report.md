# Capstone Report — CTR / Engagement Opportunity Scoring

- **Author:** Manaswini Reddy
- **Lane:** CTR / Engagement Opportunity Scoring
- **Repo:** https://github.com/manaswini1216/flyrank1
- **Date:** July 2026

---

## 0. Abstract

This project investigates how search performance signals can be used to identify content pages that deserve review. Using the FlyRank ML Internship warehouse dataset, I analyzed search visibility metrics and built a transparent baseline action scoring workflow based on search impressions, click-through rate (CTR), and average search position. The workflow ranks content pages using explainable rule-based scoring and assigns reason codes to support review decisions rather than replacing human judgment. The analysis identified high-visibility pages with unusually low CTR as the highest-priority review candidates while avoiding future information and label leakage during scoring. The final output is a ranked, explainable recommendation system that can help prioritize content review using observable search performance signals.
---

## 1. Problem framing

The goal of this project is to help identify content pages that should be reviewed because they receive high search visibility but relatively few clicks. The unit of analysis is one content page aggregated over one month of search performance data. The output is a ranked action score with a reason code and an action label that helps prioritize manual review.

A content editor or SEO analyst can use this ranked queue to decide which pages should be reviewed first for improving titles, metadata, or content. A wrong recommendation may cause time to be spent reviewing pages that are already performing well or overlook pages that actually need attention.

Machine learning and data analysis are useful because manually reviewing hundreds of thousands of pages is impractical. A transparent scoring approach provides a repeatable, explainable baseline that can later be compared against predictive models while keeping every recommendation interpretable.
---

## 2. Data safety
This project uses the public FlyRank ML Internship warehouse dataset, specifically the `fact_content_daily_performance` table. The analysis focuses on aggregated search performance metrics including impressions, clicks, click-through rate (CTR), average search position, and data availability flags.

Client identifiers (`client_hash_id`) and content identifiers (`content_hash_id`) are used only for grouping and ranking records. They are never used as predictive features. No client names, domains, URLs, search queries, or other identifying information appear anywhere in this project.

The analysis deliberately excludes any future-window information or label-derived fields to avoid data leakage. All features are computed from information that would have been available at the decision time. The final recommendations are intended for decision support rather than automated decision making.
---

## 3. Baseline

Before building any predictive model, I created a transparent rule-based baseline for identifying pages that deserve manual review. Each page receives an action score based on three observable search signals:

- High search impressions
- Low click-through rate (CTR)
- Good average search position

Pages with high visibility but unusually low CTR receive higher scores because they represent the greatest opportunity for improvement. Every recommendation includes a reason code (`LOW_CTR_VISIBLE_PAGE`) and an action label (`Review CTR & Content`) so the ranking is fully explainable.

This baseline provides a fair reference point for future machine learning models and allows every recommendation to be traced back to measurable search signals.

---

## 4. Model / analysis

This stage of the project focuses on exploratory analysis and an explainable baseline rather than a trained machine learning model. Monthly page-level aggregates were created from the daily warehouse data and used to calculate impressions, clicks, CTR, and average search position.

The main features used are:
- Total impressions
- Total clicks
- Click-through rate (CTR)
- Average search position

The target is not a supervised label but a ranked priority score indicating which pages should be reviewed first. This provides a transparent benchmark that can later be compared with supervised learning approaches while maintaining interpretability.

---

## 5. Evaluation

The baseline was evaluated by verifying that the scoring logic correctly prioritized pages with high visibility and low click-through rates. Signal validation was performed using bucket analysis for CTR versus average position and search volume.

The generated review queue ranked approximately 176,000 monthly page records and identified the highest-priority pages for manual review. Because this stage implements a rule-based baseline rather than a predictive model, no classification metrics such as accuracy or AUC are reported. Future work will compare supervised models against this baseline using the same evaluation split and metrics.

---

## 6. Interpretation

The analysis showed a consistent relationship between search visibility and click-through rate. Pages with high impressions but unusually low CTR repeatedly appeared at the top of the ranked review queue, indicating potential opportunities for improving titles, meta descriptions, or content presentation.

The bucket analysis confirmed that pages in better search positions generally achieved higher CTR, although some high-ranking pages still underperformed. This suggests that ranking alone does not guarantee user engagement.

Because this project uses an explainable rule-based baseline, every recommendation can be traced back to measurable search signals. The results are directional and intended to support content review rather than predict future search performance.

---

## 7. Recommendation

The ranked action score should be used as a decision-support tool for SEO analysts or content editors. Pages receiving the highest scores should be reviewed first because they combine strong search visibility with relatively poor click-through performance.

For each recommended page, reviewers should inspect page titles, meta descriptions, search intent alignment, and overall content quality before making changes. The assigned reason code provides a transparent explanation for why a page was prioritized.

These recommendations are based on observed historical search signals and should be combined with human judgment rather than applied automatically.

---

## 8. Reproducibility

The analysis was developed in Google Colab using DuckDB for querying the FlyRank warehouse dataset and Python for feature engineering and analysis. All notebooks used during the internship are stored under the `work/notebooks/` directory in this repository.

The workflow can be reproduced by obtaining access to the FlyRank internship dataset, creating a Hugging Face read token, connecting DuckDB to the dataset, and executing the notebooks in sequence. The generated baseline ranking can be recreated directly from the provided code without requiring any manual processing.

---

## 9. Acknowledgments & data credit

This project was completed as part of the FlyRank Machine Learning Internship.

Built using the FlyRank ML Internship dataset for educational and research purposes.

Data credit: https://flyrank.ai

The analysis follows the internship's public data usage guidelines. No client names, domains, URLs, search queries, or other identifying information are included in this repository or report.
