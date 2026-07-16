# Bank Marketing : Customer Insights Analysis


---

## Description

This project analyses a bank's phone-based marketing campaign data to understand customer behaviour and predict outcomes. The dataset contains 11,302 customer records with features such as age, account balance, and contact history. The analysis starts with exploratory data analysis to uncover patterns and distributions, followed by K-Means clustering to segment customers into distinct groups. A regression model is then built to predict how long a customer call will last, and finally a classification model predicts whether a customer will subscribe to a term deposit. Techniques used include outlier capping, log transformation, class imbalance handling, and evaluation using AUC-ROC.

---

## Project Structure

```
Bank_Marketing_Data_Analytics_and_Insights.ipynb
```

The notebook is organised into five sequential steps:

| Step | Title | Type |
|------|-------|------|
| 1 | Load Data | Setup |
| 2 | Prepare & Investigate the Data (EDA) | EDA |
| 3 | Build Customer Segmentation | Clustering |
| 4 | Predict Contact Duration | Regression |
| 5 | Predict Term Deposit Subscription | Classification |

---

## Methods & Techniques

### Step 1 : Load Data
- Dataset loaded from CSV using `pandas`
- Initial inspection: shape, column names, data types, and basic statistics
- Identification of numeric and categorical features

### Step 2 : Exploratory Data Analysis
- Statistical summaries, distribution plots, box plots, correlation heatmap
- Class imbalance detection, outlier identification, feature relationship analysis

### Step 3 : Clustering (K-Means)
- Feature standardisation with `StandardScaler`
- Optimal k selection via Elbow Method and Silhouette Score
- PCA 2D visualisation of clusters
- Customer segment profiling and business interpretation

### Step 4 : Regression
- Target: `duration` (last contact duration in seconds)
- Preprocessing: 99th percentile outlier capping + `log1p` transformation
- Models compared: Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting
- Evaluation: R² (log scale), RMSE and MAE (back-transformed to seconds)
- Feature importance analysis

### Step 5 : Classification
- Target: `TermDeposit` (binary: yes/no)
- `duration` excluded to prevent data leakage
- `class_weight='balanced'` applied to handle class imbalance (88.5% / 11.5%)
- Models compared: Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, KNN
- Primary metric: AUC-ROC (robust to class imbalance)
- Confusion matrix, ROC curves, cross-validation, feature importance

---

## Key Results

| Task | Best Model | Metric | Score |
|------|-----------|--------|-------|
| Clustering | K-Means (k=2) | Silhouette Score | 0.321 |
| Regression | Gradient Boosting | R² (log scale) | 0.0825 |
| Regression | Gradient Boosting | RMSE | 234.7s |
| Classification | Gradient Boosting | AUC-ROC | 0.7615 |
| Classification | Gradient Boosting | Accuracy | 88.2% |

---

## Dataset

- **Source**: [UCI Machine Learning Repository — Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
- **Reference**: S. Moro, R. Laureano and P. Cortez. *Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology.* ESM'2011, Guimarães, Portugal, 2011.
- **Records**: 11,302
- **Features**: 10 (age, marital, balance, day, month, duration, campaign, pdays, previous, TermDeposit)

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

Install with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## How to Run

1. Clone the repository
2. Place `bank_marketing.csv` in the same directory as the notebook
3. Open `Bank_Marketing_Data_Analytics_and_Insights.ipynb` in Jupyter
4. Run all cells top to bottom (`Kernel > Restart & Run All`)
