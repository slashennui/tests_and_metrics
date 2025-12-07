# Data Science Model Evaluation Metrics Dashboard

This repository contains a single‑page, interactive reference for common model evaluation metrics in machine learning and statistics.

The goal is to help practitioners pick appropriate metrics for their problem type and to avoid the classic failure modes that turn seemingly good models into bad decisions.

---

## Live dashboard

The dashboard is published via GitHub Pages:

- GitHub Pages: https://slashennui.github.io/tests_and_metrics/

It is implemented as a single static HTML file:

- `index.html`

No build step or server is required.

---

## Overview of content

The dashboard is organised into sections so that you can scroll or search for what you need.

### 1. Metric selection guide

A high‑level decision guide that helps you choose metrics by asking:

- Is the problem classification, regression, or hypothesis testing?
- Is the dataset balanced or imbalanced?
- Do you care about threshold‑free ranking or about performance at a specific threshold?
- For regression, do you care more about large errors or average absolute deviation?
- Do you need interpretable scores for non‑technical stakeholders?

The guide points to the relevant metric families (precision/recall, ROC AUC, F1, MAE/RMSE, etc.).

### 2. Classification metrics

For binary and multiclass classification, including:

- Accuracy and balanced accuracy  
- Precision, recall, F1  
- Specificity, false‑positive rate, false‑negative rate  
- ROC AUC and PR AUC  
- Negative predictive value (NPV)  
- Matthews correlation coefficient (MCC)  
- Cohen’s kappa  

Each metric has:

- a decision guideline (how to interpret the value range),
- a plain‑language description,
- a short explanation of how it is computed,
- an example,
- common limitations and pitfalls.

### 3. Regression and correlation metrics

For continuous targets, including:

- Mean squared error (MSE) and root mean squared error (RMSE)  
- Mean absolute error (MAE)  
- Root mean squared logarithmic error (RMSLE)  
- Correlation coefficients (Pearson, Spearman)

The focus is on when each metric is appropriate and how it can mislead (for example, high R² without useful predictions, or sensitivity of RMSE to outliers).

### 4. Inference and hypothesis testing

A compact section that covers:

- p‑values and significance thresholds  
- Confidence intervals  
- Basic tests (t‑tests, chi‑square tests, ANOVA) at a conceptual level  
- Type I and Type II errors

The emphasis is on interpretation and common misunderstandings, such as confusing a p‑value with the probability that the null hypothesis is true.

### 5. Probabilistic and calibration metrics

For models that output probabilities:

- Brier score  
- Calibration error (ECE)  
- Calibration plots

This section explains the difference between:

- ranking quality (ROC/PR AUC), and  
- probability quality (Brier score, ECE),

and why both matter for risk models.

### 6. Confusion‑matrix explorer

The page includes a small interactive calculator where you can adjust TP, FP, FN, and TN counts and see how:

- accuracy,
- precision,
- recall,
- specificity,
- F1,
- MCC,

change together. This is meant to build intuition for how different metrics respond to class imbalance and trade‑offs.

---

## Design philosophy

The dashboard is written to be practical and human‑readable:

- Plain language first, formulas second.
- Pitfalls and robustness considerations are highlighted explicitly (for example, the “accuracy trap” on imbalanced data and misuse of p‑values).
- Qualitative color bars represent ranges such as “weak”, “moderate”, or “strong” rather than rigid universal cut‑offs.
- The focus is on how to use metrics safely in real projects, not just on definitions.

---

## Repository structure

```text
tests_and_metrics/
├── index.html   # Full dashboard (HTML + CSS + JS)
└── README.md    # Project description and usage instructions
````

All layout and logic live inside `index.html`. There is no separate build pipeline or asset directory.

---

## How to use locally

You can view the dashboard locally without installing any dependencies.

1. Clone the repository:

   ```bash
   git clone https://github.com/slashennui/tests_and_metrics.git
   cd tests_and_metrics
   ```

2. Open `index.html` in a browser:

   ```bash
   # macOS
   open index.html

   # Linux
   xdg-open index.html

   # Windows (PowerShell)
   start index.html
   ```

That is all that is required; the page is static.

---

## Status and scope

* Single‑page static HTML.
* Focuses on standard metrics for classical machine‑learning and basic statistical testing.
* Does not yet cover domain‑specific metrics (for example, ranking metrics like NDCG in information retrieval, or IoU for segmentation), or deep‑learning‑specific evaluation suites.

---

## Contributing

Contributions are welcome. Useful contributions include:

* Clarifying descriptions or examples.
* Adding new metrics that are widely used in practice.
* Improving the metric‑selection guidance and common‑pitfall notes.
* Fixing typos or layout issues.

If you would like to contribute:

1. Fork the repository.
2. Make your changes in a branch.
3. Open a pull request with a short explanation of what you changed and why.

Please keep contributions:

* tool‑agnostic (not tied to a single library or framework),
* grounded in standard practice, and
* written in clear, accessible language.

---

## Contact

For questions or suggestions:

* manu – [x34mev@proton.me](mailto:x34mev@proton.me)
