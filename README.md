# Juvenile Myopia Predictor — ML Model Comparison

## Project Overview

A comprehensive Machine Learning project comparing 7 algorithms to identify the most reliable predictors of juvenile myopia using real clinical data from a longitudinal study (1990–1995).

## Research Question

Which Machine Learning algorithm best identifies reliable predictors of juvenile myopia in children aged 5–9 years?

## Dataset

* **Source:** Longitudinal Study of Myopia Development
* **Patients:** 618 children aged 5–9 years
* **Features:** 15 clinical and lifestyle measurements
* **Target:** Myopic (1) vs Not Myopic (0)
* **Class distribution:** 13.1% myopic, 86.9% not myopic

## Class Imbalance

The dataset contains a substantial class imbalance, with myopic cases representing 13.1% of the observations compared with 86.9% non-myopic cases.

Because of this imbalance, accuracy alone may not adequately represent model performance. Particular attention was therefore given to recall for the myopic class and ROC-AUC.

## Features Used

| Feature   | Description                     |
| --------- | ------------------------------- |
| SPHEQ     | Spherical Equivalent Refraction |
| AL        | Axial Length (mm)               |
| ACD       | Anterior Chamber Depth (mm)     |
| LT        | Lens Thickness (mm)             |
| VCD       | Vitreous Chamber Depth (mm)     |
| SPORTHR   | Hours of outdoor sport per week |
| READHR    | Hours of reading per week       |
| COMPHR    | Hours of computer use per week  |
| STUDYHR   | Hours of studying per week      |
| TVHR      | Hours of TV watching per week   |
| DIOPTERHR | Total near work diopter hours   |
| MOMMY     | Mother has myopia (1=Yes)       |
| DADMY     | Father has myopia (1=Yes)       |
| AGE       | Patient age                     |
| GENDER    | Patient gender                  |

## Methodology

The project followed the following workflow:

1. Data loading and inspection
2. Exploratory Data Analysis (EDA)
3. Data preprocessing
4. Feature and target selection
5. Train-test split
6. Model training
7. Model evaluation
8. Comparison of model performance
9. Identification of influential features

## Models Compared

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. XGBoost
5. Support Vector Machine (SVM)
6. K-Nearest Neighbours (KNN)
7. Naive Bayes

## Evaluation Metrics

The models were evaluated using:

* **Accuracy:** Overall proportion of correctly classified observations.
* **Recall:** Proportion of actual myopic cases correctly identified. This was prioritised because missing a myopic case is particularly important in a screening context.
* **ROC-AUC:** Measures the model's ability to distinguish between myopic and non-myopic cases across classification thresholds.

## Results Summary

### By Accuracy

| Model               | Accuracy |
| ------------------- | -------: |
| Naive Bayes         |   86.29% |
| XGBoost             |   84.68% |
| Random Forest       |   83.06% |
| Logistic Regression |   82.26% |
| KNN                 |   82.26% |
| SVM                 |   79.84% |
| Decision Tree       |   79.03% |

### By Myopic Recall (Most Important Clinical Metric)

| Model               | Recall | Caught | Missed |
| ------------------- | -----: | -----: | -----: |
| Decision Tree       |    69% |  11/16 |      5 |
| Logistic Regression |    56% |   9/16 |      7 |
| XGBoost             |    38% |   6/16 |     10 |
| SVM                 |    38% |   6/16 |     10 |
| Naive Bayes         |    31% |   5/16 |     11 |
| Random Forest       |    31% |   5/16 |     11 |
| KNN                 |    25% |   4/16 |     12 |

### By ROC AUC

| Model               |    AUC |
| ------------------- | -----: |
| Logistic Regression | 0.8258 |
| Naive Bayes         | 0.7963 |
| Random Forest       | 0.7818 |
| XGBoost             | 0.7731 |
| SVM                 | 0.7726 |
| Decision Tree       | 0.7060 |
| KNN                 | 0.5787 |

## Key Findings

### Most Influential Predictors

1. **SPHEQ** — Strongest predictor across all models
2. **SPORTHR** — Most important modifiable protective factor
3. **DADMY** — Strongest genetic predictor
4. **AL** — Key biological predictor
5. **MOMMY** — Second genetic predictor
6. **COMPHR** — Key environmental predictor (XGBoost)

### Clinical Recommendation

Based on the dataset and evaluation set, the Decision Tree achieved the highest recall for myopic cases (69%, 11/16), making it the strongest candidate among the evaluated models in this project when prioritising sensitivity to myopia. Further validation on larger and more balanced datasets would be needed before clinical deployment or recommendations.

### Clinical Implications

Children at highest risk share these characteristics:

* Low or negative spherical equivalent (SPHEQ)
* One or both parents with myopia
* Limited outdoor activity
* Longer than average axial length
* High computer usage hours

### Preventive Recommendations

* Increase outdoor activity
* Limit screen time, especially computer use
* Regular screening for children of myopic parents
* Monitor SPHEQ closely in children approaching 0.00D

## Project Structure

```text
myopia-machine-learning/
│
├── README.md
│
├── data/
│   ├── myopia.csv
│   └── myopia_model_ready.csv
│
└── notebooks/
    ├── 01_EDA.ipynb
    ├── 02_Logistic_Regression.ipynb
    ├── 03_Decision_Tree.ipynb
    ├── 04_Random_Forest.ipynb
    ├── 05_XGBoost.ipynb
    ├── 06_SVM.ipynb
    ├── 07_KNN.ipynb
    ├── 08_Naive_Bayes.ipynb
    └── 09_Comparison.ipynb
```

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost
* Jupyter Notebook
