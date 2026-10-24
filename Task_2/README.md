# Task 1 --- Credit Scoring Model

## Overview

This project explores credit-risk classification using the **UCI Statlog
German Credit dataset** as part of the CodeAlpha Machine Learning
Internship.

The goal is to classify an applicant's credit risk from the attributes
available in the dataset. The target represents two classes: good credit
risk and bad credit risk.

## Dataset

-   **Source:** UCI Statlog German Credit Data
-   **Records:** 1,000
-   **Input features:** 20
-   **Target:** Binary credit-risk class
-   **Missing values:** The original dataset inspection recorded no
    missing values.

The raw dataset commonly uses `german.data`. Check the notebook for the
exact local path and target encoding.

## Workflow

1.  Load and inspect the dataset.
2.  Examine feature types and target distribution.
3.  Prepare categorical and numerical features.
4.  Perform feature engineering where appropriate.
5.  Split the data into training and test sets.
6.  Train and compare classification models.
7.  Evaluate predictions using classification metrics.

## Models and Evaluation

The project plan includes common classifiers such as Logistic
Regression, Decision Tree, and Random Forest. Evaluation can include
precision, recall, F1-score, and ROC-AUC.

Refer to the notebook's executed output for the final models and
measured scores; this README does not invent performance numbers.

## Tools

-   Python
-   pandas and NumPy
-   scikit-learn
-   Jupyter Notebook

## Running the Notebook

1.  Open `Task1.ipynb` in Jupyter or VS Code.
2.  Ensure the German Credit dataset is available at the path expected
    by the notebook.
3.  Install the notebook's dependencies.
4.  Run the cells in order.

## Limitations

Credit-risk classification is a decision-support exercise. Dataset
labels and model outputs are not a substitute for a complete, fair, and
legally compliant credit assessment. Check the notebook for the precise
preprocessing, split strategy, and results.
