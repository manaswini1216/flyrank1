
## 0. Abstract

This paper presents a case study on prioritizing website content for manual review using anonymized search-performance data from FlyRank's Search Intelligence warehouse. The work investigates whether interpretable search signals, including click-through rate (CTR), search position, and impressions, can identify pages that deserve attention before more complex machine learning models are introduced. Signal validation confirmed that CTR generally decreases as search position worsens, while impressions alone provide a mixed indication of optimization opportunities. Using these observations, an explainable baseline scoring rule was developed to rank pages, assign reason codes and action labels, and generate a review queue. The resulting workflow provides a transparent decision-support baseline that can be compared with future machine learning models while avoiding future-data leakage and client-identifying information.

## 1. Problem framing

Large websites contain thousands of pages, making manual content review difficult. This project investigates whether search-performance signals can prioritize pages for review

## 2. Data safety

Anonymized daily observations from FlyRank's Search Intelligence warehouse for March 2026.


## 3. Baseline

The transparent rule or score you built first. Why it's a fair comparison, and its numbers on
the same data and metric as your model.

## 4. Model / analysis

Validated two search signals (CTR vs. position and impressions), then built an interpretable baseline rule combining search visibility with the gap between observed and expected CTR. Generated a ranked review queue with one reason code and one action label per page.

## 5. Evaluation
Weighted CTR across average-position buckets.

## 6. Interpretation

The baseline identified high-visibility pages with lower-than-expected CTR and produced a transparent ranked queue for manual review.

## 7. Recommendation

Use this baseline as the first stage of content prioritization and compare future ML models against it for improvements in ranking quality.

## 8. Reproducibility

The exact commands to re-run everything from a fresh clone, your random seeds, and your
environment (`pip freeze` highlights or `requirements.txt` deltas). If you claim a sealed or
holdout evaluation, two things must be committed: the cell/script that builds the sealed
frame, and the metrics file it produced — "evaluated once, blind" should be checkable from
your repo, not taken on faith.

## 9. Acknowledgments & data credit

This project was completed as part of the FlyRank Machine Learning Internship and is based on the anonymized FlyRank ML Internship dataset. The work uses public-safe search-performance data for educational and research purposes. Data source: https://flyrank.ai

---

