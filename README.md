# UrbanNest Health Analytics — Predicting Medical Insurance Charges

A data science capstone project built for a simulated healthcare analytics engagement.
The goal: help an insurance company move from rough, assumption-based pricing to a
data-driven model that predicts a patient's insurance charges from their attributes.

## Business Problem

UrbanNest Health Analytics works with insurance providers whose pricing is currently
based on general assumptions rather than data — leading to some customers being
overcharged and others undercharged. This project builds a Linear Regression model
that predicts insurance charges from patient attributes, giving the business a
transparent, data-backed starting point for fairer, more consistent pricing.

## Dataset

The [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) —
1,337 patient records with no missing values or duplicates, containing:
`age`, `sex`, `bmi`, `children`, `smoker`, `region`, and `charges`.

## Workflow

1. **Data cleaning** — checked for missing values and duplicates (none found)
2. **Exploratory Data Analysis** — visualized how each patient attribute relates to cost
3. **SQL analysis** — queried the cleaned dataset to answer cost-driver questions (see `medical_insurance_analysis.sql`)
4. **Feature preparation** — encoded categorical variables, split into train/test sets
5. **Modeling** — trained a Linear Regression model (plus a Random Forest comparison)
6. **Evaluation** — scored the model and interpreted results in business terms

## Key Findings

- **Smoking status is the single biggest cost driver.** Smokers pay **$32,050** on
  average vs. **$8,441** for non-smokers — nearly 4x more.
- **Obesity and smoking compound, rather than add up.** An obese smoker pays **$41,558**
  on average, far more than either factor would predict alone.
- Age and BMI both push charges up steadily; sex, region, and number of children have
  only minor effects.

## Model Results

| Metric | Value |
|---|---|
| R² Score | 0.81 |
| Mean Absolute Error (MAE) | $4,177 |
| Root Mean Squared Error (RMSE) | $5,956 |

The model explains about **81% of the variation** in insurance charges using only
six patient attributes. The strongest driver in the model's own coefficients is
smoking status (+$23,078 on predicted charge), followed by number of children, BMI,
and age.

## Business Recommendation

Use the model's coefficients as the basis for clearer, tiered pricing rules
(e.g. smoker vs. non-smoker, BMI category), and treat the ~$4,177 average error
margin as the built-in uncertainty of any quote — a transparent improvement over
unstructured, assumption-based pricing.

## Repo Contents

- `insurance_charge_prediction.ipynb` — full analysis notebook (cleaning, EDA, modeling, evaluation)
- `medical_insurance_analysis.sql` — SQL queries answering key business questions
- `report.pdf` — written summary of findings and recommendations *(coming soon)*
- `slides.pdf` — presentation deck *(coming soon)*

## Tools Used

Python (pandas, NumPy, matplotlib, scikit-learn), SQL
