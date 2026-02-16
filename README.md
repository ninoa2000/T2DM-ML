# Chronic Disease Risk Prediction (Type 2 Diabetes) — Dalian University Internship Project

This repository contains my internship project work completed under **Dalian University**, focused on preparing real clinical + metabolic (fatty-acid) data and developing a machine learning pipeline to **predict Type 2 Diabetes (T2DM) risk**.

The project includes:
- A **backend** service (Maven / Java) under `backend [chronic-disease]`
- A **frontend** application under `frontend`
- A **prediction** module under `prediction` for data preprocessing + ML model training/inference
- Database scripts for health/diabetes tables under `db_health.sql` and `diabetes_disease.sql`

---

## Project Aim

To develop a structured system that:
- Loads raw clinical/metabolic data
- Cleans and standardises it (missing values, garbage values, outliers, type conversion)
- Applies feature selection (ANOVA F-test as an exploratory baseline)
- Trains and evaluates machine learning models (e.g., MLP, Random Forest, Decision Tree; planned/extended: XGBoost, SVM)
- Supports a platform workflow where predictions can be served to an application layer

---

## Key Work Completed (Internship Manual Highlights)

### Data Preprocessing
The raw dataset contained missing values, inconsistent formats, and biologically unrealistic entries. Preprocessing included:
- Column name standardisation (lowercase, underscores, remove extra spaces)
- Cleaning **garbage values** (symbols like `<` `>` and placeholder/non-numeric tokens)
- Missing value analysis (using summary counts + missingness visualisation)
- Missing value handling:
  - Remove rows with >50% missingness
  - Median imputation for numeric features (robust for skewed metabolic data)
  - Mode imputation for categorical features
- Outlier detection and correction:
  - Negative fatty acid values treated as invalid
  - Age validation (below 1 or above 120 treated as missing)
  - IQR-based capping to reduce extreme values without deleting large volumes of data
- Data type conversions to ensure model-ready numeric inputs
- Z-score standardisation for numeric features (excluding the target label)

### Feature Selection (Exploratory)
- Implemented **ANOVA F-test** to rank numeric features by association with T2DM outcome
- Documented strengths and limitations:
  - Useful baseline for screening
  - Limited due to assumptions + inability to capture nonlinear interactions

### Machine Learning Models
- Implemented baseline models and evaluation workflows, including:
  - **MLP Classifier (Neural Network)** for nonlinear metabolic patterns
  - **Decision Tree**
  - **Random Forest** (best performing in my current results)
- Ongoing work: XGBoost and SVM + testing additional algorithms

---

## Repository Structure

