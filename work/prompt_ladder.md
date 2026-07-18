# Prompt Ladder

## Baseline

### Prompt

Analyze this dataset.

### Output (excerpt)

The dataset contains multiple columns and can be analyzed using summary statistics, visualizations, and machine learning techniques.

---

## Version 1 — Clear Goal

### Prompt

Analyze this dataset and identify the most important insights.

### Output (excerpt)

The response focused on identifying trends instead of giving a generic overview.

### Notes

- Layer added: Clear goal
- What improved: The response became more focused on insights.
- What still failed: It did not know who the analysis was for.
- Next change: Define the audience.

---

## Version 2 — Audience

### Prompt

Analyze this dataset and identify the most important insights for a machine learning intern.

### Output (excerpt)

The explanation focused on practical observations instead of business language.

### Notes

- Layer added: Audience
- What improved: The response became more relevant to an ML learner.
- What still failed: The dataset context was still missing.
- Next change: Add context.

---

## Version 3 — Context

### Prompt

Analyze this SEO performance dataset and identify the most important insights for a machine learning intern building a content prioritization workflow.

### Output (excerpt)

The response discussed impressions, CTR, and average position instead of giving generic advice.

### Notes

- Layer added: Context
- What improved: The analysis became specific to the project.
- What still failed: The output format was inconsistent.
- Next change: Specify the format.

---

## Version 4 — Output Format

### Prompt

Analyze this SEO performance dataset and identify the most important insights for a machine learning intern building a content prioritization workflow. Present the answer as bullet points followed by recommendations.

### Output (excerpt)

The response became organized and easier to read.

### Notes

- Layer added: Output format
- What improved: The answer became structured.
- What still failed: Some recommendations were generic.
- Next change: Add quality criteria.

---

## Version 5 — Quality Criteria

### Prompt

Analyze this SEO performance dataset and identify the most important insights for a machine learning intern building a content prioritization workflow. Present the answer as bullet points followed by recommendations. Every recommendation must reference at least one dataset metric and avoid assumptions.

### Output (excerpt)

Each recommendation was supported by dataset metrics, making the analysis more reliable.

### Notes

- Layer added: Quality criteria
- What improved: Very little changed. The response was still too generic because the audience was not defined.
- What still failed: Some explanations were longer than necessary.
- Next change: Keep responses concise.

---

# Final Prompt

Analyze an SEO performance dataset and identify the most important insights for a machine learning intern building a content prioritization workflow. Present the answer as bullet points followed by recommendations. Every recommendation must reference at least one dataset metric, avoid unsupported assumptions, and keep explanations concise.
