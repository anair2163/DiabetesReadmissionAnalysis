# 30-Day Readmission Risk Analysis

This project analyzes 30-day hospital readmission risk using the UCI Diabetes 130-US Hospitals dataset. The business question is straightforward: which patient, encounter, and utilization patterns are most associated with readmission within 30 days, and how can those insights support discharge planning and care management decisions?

The main analysis is contained in `notebooks/readmission_analysis.ipynb`. The notebook covers data loading, data dictionary review, cleaning and preprocessing, descriptive readmission analysis, utilization and operational drivers, an interpretable logistic regression model, feature interpretation, and an executive summary.

## Dataset

This project uses the UCI Diabetes 130-US Hospitals dataset and the accompanying ID mapping file:

- `diabetic_data.csv`
- `IDS_mapping.csv`

Place both files in `data/raw/` before running the notebook. Raw data is not committed to GitHub, so these files must be added locally.

## Setup

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Start Jupyter:

```bash
jupyter lab
```

3. Open `notebooks/readmission_analysis.ipynb`.

## Key Analyses

- Descriptive 30-day readmission rates across demographic and encounter segments
- Operational driver analysis for prior utilization, medication burden, and diabetes treatment signals
- Logistic regression modeling with interpretable coefficients for readmission risk
- Executive summary and recommendations for hospital operations and care management teams

## Limitations

- The analysis is observational and identifies associations, not causal effects.
- Important drivers such as social needs, outpatient follow-up, and local workflow factors are not available in the source dataset.
- The model is intentionally simple and interpretable, so it is useful for explanation but not optimized as a production prediction system.
