# People Analytics — Voluntary Turnover Prediction

> Can machine learning predict which employees will leave — before they do?

Built as part of the MBA in AI & Analytics at FGV (2026), this project applies supervised classification to a real HR dataset from a biotech company to predict voluntary turnover and support proactive retention strategies.

---

## Business context

| Metric | Value |
|--------|-------|
| Employees in dataset | 1,470 |
| Voluntary turnover rate | 16.1% (237 employees) |
| Estimated replacement cost | 2× annual salary per employee |

Identifying high-risk employees before they leave allows HR to act on retention levers — compensation, management quality, workload — before the cost is incurred.

---

## Methodology

**1. Exploratory Analysis**
Key signals identified: overtime, marital status (single = higher risk), department (Sales & R&D), and below-market salary.

**2. Preprocessing**
- 1,470 observations · 31 features · zero missing values
- Categorical encoding for model compatibility

**3. Class Imbalance**
SMOTE applied exclusively to the training set (863 vs 863), preserving the original imbalance in the test set for realistic evaluation.

**4. Modeling**
Four classifiers trained and compared, with threshold optimization by F1-Score to balance Precision and Recall.

---

## Results

| Model | F1-Score | AUC-ROC | Precision | Recall |
|-------|----------|---------|-----------|--------|
| Logistic Regression | 0.423 | 0.716 | 0.356 | 0.521 |
| Random Forest | 0.415 | 0.712 | 0.312 | 0.620 |
| **XGBoost** ✅ | **0.425** | **0.711** | **0.413** | 0.437 |
| MLP Neural Network | 0.303 | 0.596 | 0.211 | 0.535 |

**Recommended model: XGBoost** — best F1-Score and highest Precision, minimizing false alarms while capturing true flight risks.

---

## Key drivers of turnover

| Feature | Importance | Business interpretation |
|---------|------------|------------------------|
| Stock Options | 9.74% | No equity = weak long-term commitment |
| Salary | 6.31% | Below-market pay is a direct trigger |
| Job Satisfaction | 5.27% | Dissatisfied employees don't wait to leave |
| Time with Manager | 4.91% | People leave managers, not companies |
| Social Satisfaction | 4.43% | Interpersonal climate influences retention |

---

## Business recommendations

1. Extend stock option programs to operational roles
2. Conduct salary review in Sales and R&D departments
3. Launch mentorship program for single employees in their first 2 years
4. Monitor and limit excessive overtime
5. Run quarterly engagement surveys with fast-response protocols
6. Deploy monthly employee risk scoring using the XGBoost model

---

## Files

| File | Description |
|------|-------------|
| `PeopleAnalytics_Turnover.ipynb` | Full analysis notebook |
| `PeopleAnalytics_Report.pdf` | Executive presentation |
| `RH_Turma.xlsx` | Dataset |

---

## Stack

`Python` `scikit-learn` `XGBoost` `imbalanced-learn` `pandas` `numpy` `matplotlib` `seaborn` `Jupyter Notebook`

