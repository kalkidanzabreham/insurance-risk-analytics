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
├── dvc.yaml # Pipeline definition
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
