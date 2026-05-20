# Customer Churn Risk Modelling

A machine learning project that predicts which Telco customers are likely to cancel their subscription, built with a focus on making the model useful for real retention decisions.

**Author:** Khaliq Lamid

---

## What this project does

When a customer cancels a subscription, getting them back costs far more than keeping them. The earlier a business can spot who's likely to leave, the more time it has to act.

This project builds a model that does exactly that. It takes customer data, like contract type, payment method, how long they've been a customer, and what services they use, and predicts whether they're at risk of churning. The model doesn't just output a yes or no; it outputs a probability, and a key part of this project is tuning where to draw the line between "flag this customer" and "leave them alone."

## What's in this repo

- `Customer_Churn_Risk_Modelling.ipynb` — the full notebook, with explanations for every decision made
- `Telco_Customer_Churn.csv` — the dataset (publicly available)
- `README.md` — this file

## How it works

The pipeline runs in nine steps:

1. **Data loading** — spotting that `TotalCharges` was stored as text instead of a number, which would break any model trained on it
2. **Exploratory analysis** — looking at churn rates across contract type, internet service, payment method, tech support, tenure, and monthly charges
3. **Data cleaning** — fixing the `TotalCharges` column and handling the 11 zero-tenure customers with no billing history
4. **Feature encoding** — converting categorical columns into numeric format the model can read
5. **Modelling** — training and comparing two classifiers: Logistic Regression and Random Forest
6. **Evaluation** — using Precision, Recall, F1-score, and ROC-AUC; accuracy alone is misleading when only 27% of customers churned
7. **Threshold tuning** — testing cut-offs from 0.30 to 0.50 to find the point that catches the most churners without too many false alarms
8. **Feature importance** — reading the Logistic Regression coefficients to see which features actually drive the predictions
9. **Model saving** — storing the trained model with joblib so it can be reused without retraining

## What the model found

A few features stand out as strong churn signals:

**Higher churn risk:** fibre optic internet, streaming movies, multiple lines, paperless billing, electronic check payments, senior citizens

**Lower churn risk:** two-year contracts, online security, tech support, having dependents, no internet service

These aren't surprising, but the model puts numbers to them. The Logistic Regression coefficients show that fibre optic internet (1.05) and two-year contracts (-1.38) are by far the two strongest signals in opposite directions.

## Why threshold tuning matters

By default, a classifier flags a customer as "churning" when its predicted probability hits 0.5 or above. That's a reasonable default, but it's not always the right one.

In a retention context, missing a churner costs more than flagging someone who would've stayed. Lowering the threshold to around 0.40 catches more at-risk customers, with only a modest drop in precision. The notebook tests a range of cut-offs and shows where that trade-off makes the most practical sense.

## Tools used

- Python 3
- pandas, NumPy
- scikit-learn (LogisticRegression, RandomForestClassifier, metrics, train_test_split)
- joblib

## Limitations

- The dataset has roughly 7,000 rows, which is workable but small for a real deployment
- All exploratory analysis is tabular; charts would make the patterns easier to communicate
- More powerful models like XGBoost weren't tested here but would be a natural next step

## Reflection

The threshold tuning section was the most instructive part of this project. Changing one number changed which customers the model flagged, and getting that decision right required thinking about what a missed churner actually costs, not just chasing a better F1-score. That gap between optimising a metric and solving a business problem is worth keeping in mind.
