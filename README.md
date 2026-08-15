# Data Science Model Evaluation Metrics Dashboard

An interactive, single-page reference for model evaluation, statistical testing, robustness, diagnostics, model selection, calibration, and interpretability.

**Live dashboard:** https://slashennui.github.io/tests_and_metrics/

The dashboard is intentionally practical: formulas and definitions are paired with interpretation guidance, common failure modes, interactive playgrounds, and executable Python examples.

---

## What the dashboard covers

### Classification
- Accuracy, precision, recall/sensitivity, specificity
- False-positive and false-negative rates
- F1 score
- Balanced accuracy
- ROC AUC
- Precision-recall curves, Average Precision (AP), and PR AUC
- Negative predictive value
- Cohen's kappa
- Matthews correlation coefficient (MCC)
- Brier score and calibration error

For multiclass problems, class-specific metrics need an averaging or aggregation rule (for example macro, weighted, micro, or one-vs-rest). The dashboard calls out when a displayed formula is specifically binary.

### Survival / time-to-event analysis
- Kaplan-Meier curves
- Log-rank testing
- Cox proportional-hazards models
- Concordance index
- Time-dependent AUC
- Time-dependent Brier scores
- Censoring, competing risks, proportional-hazards assumptions, and immortal-time bias

### Inference and statistical testing
- p-values and confidence intervals
- Type I / Type II error and power
- Welch and classical t-tests
- ANOVA / Welch ANOVA
- Chi-square and Fisher's exact tests
- Permutation tests
- Multiple-testing control: Bonferroni and Benjamini-Hochberg
- Effect sizes including Cohen's d and Cliff's delta

### Robustness and resampling
- Cross-validation
- Bias-variance trade-off
- Bootstrap confidence intervals
- Delete-1 jackknife standard errors
- Resampling stability
- Feature-selection stability
- Interactive bootstrap-vs-jackknife demonstrations

### Validation, uncertainty, and deployment
- Stratified, grouped, temporal, spatial, nested, and external validation principles
- Training-fold-only preprocessing and feature-selection discipline
- Validation-set threshold selection before final untouched test evaluation
- Design-appropriate uncertainty estimation and resampling
- Subgroup checks, label/data quality, leakage, and post-deployment drift

### Regression and correlation
- R² and adjusted R²
- MAE, MSE, RMSE, RMSLE
- Pearson, Spearman, and partial correlation
- Regression coefficients and uncertainty
- Durbin-Watson, Breusch-Pagan, and residual normality diagnostics

### Multicollinearity and influence
- Variance Inflation Factor (VIF)
- Condition number
- Cook's Distance
- Mahalanobis distance
- Z-score, robust MAD score, and Tukey/IQR outlier rules
- Interactive influence, leverage, VIF, and multiple-testing demonstrations

### Model selection
- AIC / AICc
- BIC
- Mallows' Cp
- Cross-validated deviance / log-loss
- Regularisation strength

### Interpretability and advanced diagnostics
- Permutation feature importance
- SHAP
- LIME
- Calibration diagnostics
- Distribution-shift diagnostics
- Bayesian predictive comparison
- Predictive uncertainty
- Fairness diagnostics
- Leakage checks

---

## Interpretation philosophy

The dashboard deliberately avoids treating most numeric cut-offs as universal laws.

A metric should normally be interpreted against:
- a task-relevant baseline,
- uncertainty or resampling variability,
- class prevalence,
- operating thresholds,
- decision costs,
- the data-generating structure,
- and standards in the relevant domain.

Where familiar numeric bands are shown (for example Cohen's d, Cook's Distance, VIF, or correlation magnitude), they are labelled as conventions or screening heuristics rather than universal pass/fail criteria.

A p-value is evidence relative to a specified null model and test assumptions; it is not the probability that the null hypothesis is true, an effect size, or an intrinsically "good" or "bad" result.

---

## Interactive tools

The page includes:
- a binary confusion-matrix explorer,
- a bootstrap-vs-jackknife stability playground,
- an outlier-impact regression playground,
- a Cook's Distance / leverage playground,
- a clearly labelled toy noise-sensitivity illustration,
- a Bonferroni family-wise-error demonstration,
- and an equicorrelation VIF demonstration.

The confusion-matrix explorer reports mathematically undefined ratios as `NA` rather than silently converting them to zero.

---

## Executable notebook examples

The dashboard links to Binder-ready companion repositories for:
- classification metrics and confusion matrices,
- statistical tests,
- regression metrics,
- SHAP and LIME.

Those notebooks are intended to be standalone and reproducible: they use self-contained generated or bundled example data, apply appropriate train/evaluation separation where predictive models are fitted, use current APIs, and do not rely on hidden notebook state.

---

## Repository structure

```text
tests_and_metrics/
├── index.html   # Full dashboard: HTML + CSS + JavaScript
└── README.md    # Project documentation
```

There is no build system. The page is static, but it loads MathJax and syntax-highlighting assets from CDNs and contains an optional collapsed Spotify embed; an internet connection is required for those external assets. Binder launch badges also depend on the external Binder service.

---

## Run locally

The simplest preview that behaves like a hosted site is:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/`.

You can also open `index.html` directly in a browser, although serving it locally is preferable when checking browser behaviour.

---

## Selected technical references

The dashboard includes a short, non-exhaustive reference section. Core implementation/documentation sources include:
- [scikit-learn: Model selection and evaluation](https://scikit-learn.org/stable/model_selection.html)
- [scikit-learn: Probability calibration](https://scikit-learn.org/stable/modules/calibration.html)
- [SciPy: Statistical functions](https://docs.scipy.org/doc/scipy/reference/stats.html)
- [SHAP paper](https://arxiv.org/abs/1705.07874)
- [LIME paper](https://arxiv.org/abs/1602.04938)
- [Binder: Configure the user interface](https://mybinder.readthedocs.io/en/latest/howto/user_interface.html)

---

## Scope and limitations

This is a practical reference, not a substitute for a statistical analysis plan or domain-specific validation standard.

The dashboard focuses on broadly used classical-statistics and machine-learning evaluation tools. It does not attempt to cover every specialised family, including forecasting scores, information-retrieval/recommender ranking metrics, clustering validation, multilabel evaluation, computer-vision segmentation metrics, language-model evaluation suites, reinforcement-learning evaluation, or every causal-inference diagnostic.

Interactive playgrounds that use illustrative heuristics are explicitly labelled as such and should not be interpreted as estimators or formal hypothesis tests.

---

## Contributing

Contributions are welcome. Useful contributions include:
- correcting definitions or assumptions,
- improving examples and code,
- adding well-established metrics,
- improving accessibility or layout,
- and adding citations or domain-specific cautions.

Please keep contributions:
- technically reproducible,
- explicit about assumptions,
- clear about whether a threshold is a convention or a theorem,
- and written in accessible language.

---

## Contact

manu — [x34mev@proton.me](mailto:x34mev@proton.me)
