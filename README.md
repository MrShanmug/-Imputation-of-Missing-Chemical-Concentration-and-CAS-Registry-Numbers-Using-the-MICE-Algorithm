# -Imputation-of-Missing-Chemical-Concentration-and-CAS-Registry-Numbers-Using-the-MICE-Algorithm
 Imputation of Missing Chemical Concentration and CAS Registry Numbers Using the  MICE Algorithm
# Imputation of Missing Chemical Concentration and CAS Registry Numbers Using MICE

## Project Overview

Incomplete chemical product records can negatively impact regulatory compliance, hazard assessment, exposure analysis, and inventory management. This project evaluates the effectiveness of Multiple Imputation by Chained Equations (MICE) in recovering missing values for two critical fields:

* CAS Registry Number
* Chemical Concentration

The study establishes a reproducible machine learning workflow and evaluates imputation performance under controlled missing-data scenarios.

---

## Business Problem

Chemical manufacturers and regulatory organizations depend on accurate chemical records for safety and compliance. Missing CAS Numbers and concentration values introduce uncertainty into reporting processes and downstream analytics.

Traditional methods such as manual review and simple statistical imputation are often inefficient and fail to leverage relationships within the data. This project investigates whether machine learning-based imputation can improve data completeness and quality.

---

## Research Objectives

1. Evaluate the ability of MICE to recover missing CAS Number and Concentration values.
2. Compare joint imputation of CAS Number and Concentration against Concentration-only imputation.
3. Identify challenges associated with imputing high-cardinality categorical variables.

---

## Dataset

The dataset contains chemical product records with the following attributes:

* Trade Name
* Chemical Name
* CAS Number
* Concentration

### Dataset Statistics

| Attribute                   | Count  |
| --------------------------- | ------ |
| Total Records               | 16,703 |
| Total Features              | 4      |
| Unique Trade Names          | 6,557  |
| Unique Chemical Names       | 3,200  |
| Unique CAS Numbers          | 1,844  |
| Unique Concentration Values | 743    |

---

## Methodology

### Data Preparation

* Schema validation
* Data quality checks
* Train-test split (80/20)
* Controlled masking of test records
* Categorical encoding

### Modeling

The project uses the Scikit-learn IterativeImputer implementation of Multiple Imputation by Chained Equations (MICE).

Model Configuration:

* Random State = 42
* Maximum Iterations = 50

### Evaluation Metrics

Performance is evaluated only on masked values using:

* Accuracy
* Macro F1 Score

---

## Experimental Scenarios

### Scenario 1: Both Targets Missing

Both CAS Number and Concentration values are masked simultaneously and then imputed.

### Scenario 2: Concentration Only Missing

Only Concentration values are masked while CAS Number remains available.

---

## Results Summary

| Scenario           | Target        | Accuracy (%) | Macro F1 (%) |
| ------------------ | ------------- | ------------ | ------------ |
| Both Missing       | CAS Number    | 0.00         | 0.00         |
| Both Missing       | Concentration | 0.75         | 0.20         |
| Concentration Only | Concentration | 0.75         | 0.24         |

### Key Findings

* Concentration values were easier to recover than CAS Numbers.
* MICE struggled with high-cardinality categorical identifiers.
* Ordinal encoding introduced artificial relationships between categories.
* The framework provides a reproducible baseline for future research.

---

## Deployment Considerations

A production implementation could be deployed as a batch-processing service within a chemical registry management platform.

Potential deployment options include:

* AWS SageMaker
* Azure Machine Learning
* Docker-based API Services
* On-Premises Python Applications

Recommended monitoring metrics:

* Imputation Accuracy
* Data Completeness Rate
* Model Drift
* Regulatory Audit Exceptions

---

## Repository Structure

```text
├── data/
│   ├── raw/
│   ├── processed/
│
├── notebooks/
│   ├── MICE_Imputation_Project.ipynb
│
├── reports/
│   ├── Final_Project_Report.pdf
│
├── presentation/
│   ├── Final_Presentation.pptx
│
├── src/
│   ├── preprocessing.py
│   ├── modeling.py
│   ├── evaluation.py
│
├── requirements.txt
├── README.md
└── LICENSE
```

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Jupyter Notebook
* python-docx

---

## Future Work

Future research will evaluate alternative approaches including:

* Random Forest Imputation
* MissForest
* CatBoost
* XGBoost
* Deep Learning Autoencoders
* Retrieval-Augmented Imputation Systems

These methods may improve performance for high-cardinality categorical variables such as CAS Registry Numbers.

---

## Authors

**Purushothama V S**
University of San Diego

**Shanmug Bhanu Prakash**
University of San Diego

AAI 510 – Machine Learning Fundamentals

Instructor: Anamika Singh

June 2026
