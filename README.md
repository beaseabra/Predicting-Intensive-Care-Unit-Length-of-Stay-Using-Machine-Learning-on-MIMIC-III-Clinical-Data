# ICU Length of Stay Prediction using MIMIC-III and Google Cloud

## Overview

This project develops an end-to-end Data Engineering and Machine Learning pipeline to predict Intensive Care Unit (ICU) Length of Stay (LOS) using the MIMIC-III clinical database.

The project combines large-scale cloud data processing with predictive analytics, leveraging Google Cloud Platform (BigQuery and Google Cloud Storage), Google Colab, and modern Machine Learning techniques.

The work is divided into three phases:

- Phase 1 – Data Engineering and Feature Construction
- Phase 2 – Length of Stay Regression
- Phase 3 – Prolonged Stay Risk Classification

---

## Authors

- Beatriz Seabra
- Iara Ferreira

Faculty of Sciences, University of Porto (FCUP)

---

## Dataset

The project uses the MIMIC-III (Medical Information Mart for Intensive Care III) database, containing anonymized clinical records from ICU patients.

Main tables used:

- CHARTEVENTS
- ICUSTAYS
- PATIENTS
- D_ITEMS
- INPUTEVENTS_MV

---

## Technology Stack

### Cloud Infrastructure

- Google BigQuery
- Google Cloud Storage (GCS)
- Google Colab

### Data Processing

- Python
- Pandas
- NumPy

### Machine Learning

- Scikit-Learn
- LightGBM
- XGBoost

### Visualization

- Matplotlib
- Seaborn

---

## Phase 1 – Data Engineering

The first phase focused on extracting, cleaning, validating, and transforming clinical data.

Key steps included:

- Large-scale querying in BigQuery
- Clinical variable selection
- Data cleaning and physiological outlier removal
- Missing value analysis
- Exploratory Data Analysis (EDA)
- Temporal window comparison
- Feature engineering
- Construction of the final feature matrix

### Final Dataset

- 59,057 ICU stays
- 44,940 unique patients
- 57 predictive features
- 24-hour observation window selected

---

## Phase 2 – Length of Stay Regression

The second phase aimed to predict ICU Length of Stay as a continuous variable.

Models evaluated:

- Linear Regression
- Ridge
- ElasticNet
- Random Forest
- HistGradientBoosting
- XGBoost
- LightGBM

### Best Model

**LightGBM with log-transformed target**

Performance:

- MAE ≈ 3.11 days
- RMSE ≈ 8.43
- R² ≈ 0.25

The final model achieved approximately **17% improvement** over the baseline predictor.

---

## Phase 3 – Prolonged Stay Risk Classification

The final phase reformulated the problem as a binary classification task.

Targets evaluated:

- LOS ≥ 7 days
- LOS ≥ 14 days
- LOS ≥ 30 days

Temporal windows compared:

- 6 hours
- 12 hours
- 24 hours
- 48 hours

### Best Configuration

**HistGradientBoostingClassifier**

- 48-hour window
- LOS ≥ 7 days target

Performance:

- AUPRC = 0.6105
- AUROC = 0.8961
- F1-Score = 0.6167

---

## Key Findings

- ICU Length of Stay can be predicted using only early clinical measurements.
- Monitoring intensity variables were among the strongest predictors.
- Heart Rate monitoring frequency consistently appeared as one of the most important features.
- A 24-hour window provides the best balance between prediction timeliness and performance.
- A 48-hour window achieves the highest predictive performance.

---

## Repository Structure

```text
.
├── Fase1_final_final.ipynb
├── Fase2_final_final.ipynb
├── Fase3_final_final.ipynb
├── Relatorio_MIMIC3_UCI_final.pdf
└── README.md
```

---

## Results Summary

| Task | Best Model | Main Metric |
|--------|------------|------------|
| LOS Regression | LightGBM | MAE ≈ 3.11 days |
| Risk Classification | HistGradientBoosting | AUROC ≈ 0.90 |

---

## Disclaimer

MIMIC-III access requires credentialing and compliance with PhysioNet data usage policies.

This project was developed for academic and research purposes.
