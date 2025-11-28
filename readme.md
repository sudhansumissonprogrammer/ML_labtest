📌 Loan Default Prediction — FinSecure Risk Modeling Project
🏦 Project Overview

This project focuses on building a data-driven loan default prediction system for FinSecure, a peer-to-peer lending platform that connects borrowers with investors.
The goal is to help the company identify high-risk loan applications, reduce financial losses, and improve trust in the lending marketplace.

FinSecure currently relies on a manual, scorecard-based approval workflow. This traditional approach is slow, limited, and unable to capture complex patterns across borrower attributes.
To modernize the process, we develop a machine learning model capable of predicting whether a loan will be paid back (1) or default (0) using borrower and loan characteristics.

📂 Dataset Description

The dataset used in this project is loan_data.csv, containing historical loan applications with the following attributes:

Borrower & Loan Features

id — Unique loan identifier

annual_income — Annual income of the applicant

debt_to_income_ratio — Total debt divided by annual income

credit_score — Borrower’s credit score

loan_amount — Requested loan amount

interest_rate — Assigned interest rate

gender — Borrower’s gender

marital_status — Marital status

education_level — Highest education attained

employment_status — Current employment status

loan_purpose — Purpose of the loan (e.g., debt consolidation, home improvement)

grade, subgrade — Internal risk indicators assigned by FinSecure

Target Variable

loan_paid_back

1 → Loan fully paid back

0 → Loan default / not repaid

🎯 Section 1 — Problem Formulation & Target Variable

The business problem:

Predict whether a borrower will default on their loan.

Here, default means loan_paid_back = 0, i.e., the borrower fails to fully repay the loan.
The model must output a probability of repayment/default for each loan application.

🛠️ Section 2 — Feature Engineering & Preprocessing Pipeline

A complete ML preprocessing pipeline is designed to include:

✔ Handling Missing Values

Numerical features → Median imputation

Categorical features → Most frequent value imputation

✔ Categorical Encoding

Encoded using One-Hot Encoding (or Ordinal Encoding depending on the variable)

✔ Numerical Feature Scaling

Numerical variables like annual_income, loan_amount, etc. are normalized using
StandardScaler or MinMaxScaler to improve model performance.

✔ Train–Test Split

The dataset is split into training and testing sets to evaluate model generalization.

All preprocessing is wrapped inside a scikit-learn Pipeline to avoid data leakage.

🤖 Section 3 — Model Development & Hyperparameter Tuning

The task is framed as a binary classification problem.
The model predicts a probability for the target loan_paid_back.

✨ Modeling Steps

Baseline + advanced models tested (e.g., Logistic Regression, Random Forest, XGBoost)

Hyperparameter tuning performed using GridSearchCV + Stratified K-Fold CV

Evaluation metric: ROC AUC

Measures how well the model ranks high-risk vs low-risk borrowers

Ideal for imbalanced datasets common in loan default prediction

The final model outputs a probability of loan repayment, enabling risk-based decisions.

⚖️ Section 4 — Subgroup Fairness Analysis

To ensure the model treats different demographic/loan-purpose groups fairly, performance is evaluated across key subgroups:

✔ By Education Level

AUC is calculated for each distinct education category:

High School

Bachelor

Master

etc.

✔ By Loan Purpose

AUC scores computed for each purpose category, identifying:

Top 3 performing loan purposes

Bottom 3 performing loan purposes

This helps detect whether certain groups are disproportionately misclassified.

📊 Metrics Reported

ROC AUC (global performance)

Subgroup AUC (fairness checks)

Probability outputs for each test sample (risk scoring)

🚀 Final Outcome

This project delivers a complete machine-learning solution capable of:

✔ Predicting borrower default risk
✔ Automating loan decision support
✔ Providing fairness-aware model evaluation
✔ Supporting FinSecure in building a reliable, scalable credit risk assessment system