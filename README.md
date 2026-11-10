# 30-Day Hospital Readmission After a Diabetes Encounter

Which encounters were followed by a recorded readmission within 30 days, and how well could a discharge-time model distinguish higher- and lower-risk encounters?

[Open the analysis notebook](notebooks/readmission_analysis.ipynb) · [UCI dataset and data dictionary](https://archive.ics.uci.edu/dataset/296/diabetes-130-us-hospitals-for-years-1999-2008)

## Findings

| Measure | Result |
| --- | ---: |
| Eligible encounters | 99,340 |
| Observed 30-day readmission rate | 11.4% |
| Readmission with no prior inpatient visits | 8.6% of 66,242 encounters |
| Readmission with three prior inpatient visits | 21.0% of 3,271 encounters |
| Test average precision | 0.224 vs. 0.113 prevalence benchmark |
| Test ROC-AUC | 0.666 |
| Precision and recall at the default threshold | 18.8% and 53.1% |

Prior inpatient utilization showed a clear descriptive difference. The model improved ranking over a constant-score benchmark, but its default threshold flagged substantially more encounters than ultimately had a recorded readmission. That tradeoff matters for any follow-up workflow with limited capacity.

## How the analysis works

- Use the UCI 1999–2008 encounter data. Exclude recorded deaths, discharges to hospice and invalid gender records.
- Define the target as the source's `<30` readmission category. Compare groups with the encounter counts alongside their rates.
- Fit class-weighted logistic regression with features available by discharge. Treat coded fields as categorical. Split by patient identifier, so each patient's encounters are entirely in training or test.
- Report average precision against test prevalence and show the default threshold's precision and recall. Model coefficients describe conditional associations.

The cohort is historical, and no temporal, external, calibration or subgroup validation was performed. The recorded outcome does not distinguish avoidable readmissions.

## Reproduce

Download `diabetic_data.csv` and `IDS_mapping.csv` from [UCI](https://archive.ics.uci.edu/dataset/296/diabetes-130-us-hospitals-for-years-1999-2008), place them in `data/raw/`, then run:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Open `notebooks/readmission_analysis.ipynb` and run all cells.
