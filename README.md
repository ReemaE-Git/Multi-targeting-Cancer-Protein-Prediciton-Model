# Multi-Target Breast Cancer Protein Prediction

## Project Overview
This project explores whether combinations of selected cancer-related genes can distinguish tumor samples from normal tissue using TCGA breast cancer data. The goal is to identify dual-target and triple-target gene combinations that show strong tumor specificity and may be useful for future therapeutic targeting.

## Why This Matters
Cancer is highly complex, and single-gene targeting often fails due to tumor heterogeneity. Multi-target approaches may improve treatment effectiveness by increasing tumor coverage while reducing effects on normal tissue.

## Dataset
- Source: TCGA (The Cancer Genome Atlas)
- File: denseDataOnlyDownload-2.tsv
- Loaded directly from public GitHub
- Total samples: ~1200+
- Includes:
  - Primary Tumor
  - Metastatic
  - Normal tissue

## Selected Genes
- PGR
- ERBB2
- SLAMF7
- PTEN
- EGFR
- CD276
- ICAM1

## Methodology

### 1. Data Preprocessing
- Removed missing values
- Mapped gene IDs to readable gene names
- Created binary labels:
  - 1 = Tumor
  - 0 = Normal

### 2. Statistical Analysis
- Compared tumor vs normal expression
- Used Mann-Whitney U test
- Identified key differences in gene expression

### 3. Class Imbalance Handling
- Applied custom SMOTE
- Only used within training folds to avoid data leakage

### 4. Feature Engineering
- Evaluated:
  - Dual gene combinations
  - Triple gene combinations
- Measured tumor coverage vs normal coverage

### 5. Machine Learning Models
- Logistic Regression (baseline)
- Decision Tree
- Random Forest

### 6. Evaluation
- Used Stratified K-Fold Cross Validation
- Metric: F1 Score

## Results

### Best Dual Target
SLAMF7 + CD276

### Best Triple Target
ERBB2 + SLAMF7 + CD276

### Model Performance
- Random Forest performed best overall
- Indicates nonlinear relationships between gene features

## Key Insights
- Certain gene combinations strongly separate tumor from normal tissue
- Multi-target approaches may be more effective than single-gene targeting
- Nonlinear models capture biological interactions better

## Limitations
- Only 7 genes analyzed
- Synthetic data used via SMOTE
- No external validation dataset

## Future Work
- Expand gene pool
- Validate with additional datasets
- Apply explainability methods (SHAP)
- Explore deep learning models

## How to Run
1. Open notebook in Google Colab
2. Run all cells
3. Dataset loads automatically from GitHub

## Technologies Used
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib
