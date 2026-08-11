# Credit Card Fraud Detection

A machine learning project detecting fraudulent credit card transactions in a
highly imbalanced dataset (~0.17% fraud). Compares Logistic Regression, Random
Forest, and Random Forest + SMOTE, then tunes the decision threshold based on
a stated business tradeoff.

## Dataset
[Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
(Kaggle) — ~285,000 transactions, 492 labeled as fraud.

**To reproduce:** download `creditcard.csv` from the link above and place it
in the `data/` folder. It's not included in this repo due to its size and
Kaggle's redistribution terms.

## How to run this
1. Clone this repo
2. `python -m venv venv` then activate it (`source venv/bin/activate` on
   Mac/Linux, `venv\Scripts\activate` on Windows)
3. `pip install pandas numpy scikit-learn matplotlib seaborn jupyter imbalanced-learn`
4. Download the dataset (see above) into `data/`
5. Open the notebooks in `notebooks/` in order (01 → 04)

## Key findings
- Only 0.17% of transactions are fraud, which makes accuracy a useless
  metric — a model predicting "not fraud" for everything would still be
  99.83% "accurate."
- Logistic Regression (with class weighting) caught 92% of fraud but had
  only 6% precision — a flood of false alarms.
- Random Forest (with class weighting) performed best overall: 92%
  precision, 81% recall, F1 of 0.86 — beating both Logistic Regression and
  Random Forest + SMOTE.
- After tuning the classification threshold to 0.57, the final model catches
  81% of fraud while flagging only 5 legitimate transactions out of nearly
  57,000 (94% precision).

## Tools
Python, pandas, scikit-learn, imbalanced-learn, matplotlib/seaborn, SQLite

## Notebooks
- `01_eda.ipynb` — exploratory data analysis, class imbalance
- `02_baseline_model.ipynb` — Logistic Regression baseline
- `03_model_comparison.ipynb` — Random Forest and SMOTE comparison
- `04_threshold_tuning.ipynb` — precision-recall tradeoff, final model, SQL queries

See `memo.md` for a plain-language summary written for a non-technical audience.