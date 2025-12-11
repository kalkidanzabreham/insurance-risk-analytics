# 🚗 Insurance Portfolio Risk Analysis 

This repository contains the deliverables for the Insurance Risk Analytics project.  
The focus is to establish strong engineering foundations through Version Control, Exploratory Data Analysis (EDA), and reproducible data management with DVC.

---

## 📁 Project Structure
```bash
.
├── data/
│ ├── raw/ # Raw input data (tracked with DVC only)
│ └── processed/ # Cleaned and transformed datasets
├── notebooks/
│ ├── 01_eda.ipynb # Exploratory Data Analysis
│ ├── 02_hypothesis_tests
│ ├── 03_modeling_task4
├── dvc.yaml # Pipeline definition
├── plots/
├── reports/
│ ├── figures/
├── requirements.txt
├── README.md
└── .gitignore

```
---


### **Task 1 — Git + EDA**
- Repository initialized and structured.
- Branch `task-1` created, work committed with meaningful messages.
- Exploratory Data Analysis performed:
  - Data understanding (dtype, missing values, structure)
  - Descriptive statistics
  - Univariate & bivariate analysis
  - Outlier detection via boxplots
  - Geographical + temporal trends
- Creative visualizations produced:
  - Radar chart for Loss Ratio by Vehicle Type  
  - Heatmap: Province × Vehicle Type  
  - Claim Frequency Area Chart

Notebook:  
📄 `notebooks/01_eda.ipynb`

---

### **Task 2 — Reproducible Data Pipeline with DVC**
- DVC installed and initialized
- Local remote storage configured
- Raw insurance dataset added with `dvc add`
- Data versioning established (v1, v2)
- Data pushed to the local remote using `dvc push`
- Branch `task-2` created and merged with a PR

Commands used:

```bash
pip install dvc
dvc init
```

# Set up local remote
```bash
mkdir -p ../dvc_storage
dvc remote add -d localstorage ../dvc_storage
```

# Track data
```bash
dvc add data/raw/insurance_data.txt
git add data/raw/insurance_data.txt.dvc .gitignore
git commit -m "Track raw insurance dataset with DVC"
```

# Push data to remote
```bash
dvc push
```

🚀 How to Reproduce the Pipeline
Clone the repository

Install requirements:

```bash
pip install -r requirements.txt
```
Pull data from DVC remote:
```bash
dvc pull
```
Open notebooks:
```bash
jupyter lab
```
### Task 3 — Hypothesis Testing & Statistical Evidence
✔ Key Analyses Performed

- T-tests comparing claim amounts across:

    - Gender
    - Fuel type
    - Vehicle type

- Chi-Square tests:

    - ClaimEvent × Region
    - ClaimEvent × Gender

- ANOVA for multi-category comparisons
- Correlation significance tests for numeric predictors

✔ Outcomes

- Clean summary table of all hypothesis tests
- File exported as:

    - hypothesis_test_summary.csv

📄 Notebook: notebooks/02_hypothesis_tests.ipynb
📄 Output: data/processed/hypothesis_test_summary.csv

### Task 4 — Predictive Modelling (Frequency, Severity, Pure Premium)
✔ 1. Data Preprocessing

- Robust memory-safe transformations
- Numeric imputation
- Categorical encoding with OneHotEncoder
- Feature engineering:

    - VehicleAge
    - VehiclePowerRatio
    - DriverExperience
    - ClaimRateByProvince


✔ 2. Frequency Modelling (Binary Classification)

Models used:
  - LogisticRegression(solver='saga') — sparse & scalable
  - Optional: XGBoost with DMatrix

Metrics:
  - ROC-AUC
  - F1
  - Precision
  - Recall
  - Accuracy

✔ 3. Severity Modelling (Regression)

Models:
  - RandomForestRegressor
  - GradientBoostingRegressor
  - Median Benchmark

Metrics:
  - RMSE
  - MAE
  - R²

✔ 4. Pure Premium Estimation

For each policy:

Pure Premium = P(ClaimEvent=1) × E[ClaimCost | ClaimEvent=1]


Computed using chunked memory-safe predictions:
  - predict_proba_chunked()
  - predict_chunked_regression()

Final output saved:
📄 data/processed/pure_premium_predictions.csv

✔ 5. Model Explainability 

  - SHAP values (TreeExplainer / LinearExplainer)
  - Feature impact visualization
  - Interpretation of primary drivers of risk


🚀 Final Deliverables
| **Component** | **Description**                                      |
|---------------|------------------------------------------------------|
| **Task 1**    | EDA + visuals + repo structure                       |
| **Task 2**    | DVC pipeline + versioned datasets                    |
| **Task 3**    | Statistical hypothesis testing + summary CSV         |
| **Task 4**    | Frequency, severity, pure premium modeling + predictions CSV |


All tasks are complete and reproducible using the instructions below.

🛠️ How to Run Everything
```bash
git clone https://github.com/kalkidanzabreham/insurance-risk-analytics
pip install -r requirements.txt
dvc pull
jupyter lab
```

📌 Notes
Raw data is never committed to Git, only tracked via DVC.
To create a new data version:

```bash
dvc add data/raw/insurance_data_v2.txt
git commit -am "Add new dataset version"
dvc push
```
✨ Author
Kalkidan Abreham — Data Science & Machine Learning
