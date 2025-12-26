# Default of Credit Card Clients  
**ASDS 6303 – Data Mining Final Project**

**Authors:** Phuong Trinh, Kyra Stolarski  
**Course:** ASDS 6303 – Data Mining  
**Institution:** University of Texas at Arlington  
**Date:** December 2025  

---

## 📌 Project Overview
Credit card default prediction is a critical problem in financial risk management. Accurately identifying clients who are likely to default allows financial institutions to reduce losses, improve credit policies, and design fairer lending strategies.

This project analyzes the **Default of Credit Card Clients** dataset from the **UCI Machine Learning Repository**, which contains demographic information, credit limits, repayment history, bill amounts, and payment behavior for **30,000 credit card holders in Taiwan**.

We develop and compare multiple classification models to predict whether a client will **default on their credit card payment in the following month**.

---

## 🎯 Objectives
- Perform data cleaning, preprocessing, and exploratory data analysis (EDA)
- Address class imbalance in default outcomes
- Build and evaluate multiple classification models:
  - Logistic Regression
  - CART Decision Tree
  - Random Forest
- Compare model performance using:
  - Confusion Matrix
  - Accuracy (Train/Test)
  - Sensitivity & Specificity
  - ROC Curve and AUC
- Provide actionable insights for credit risk assessment

---

## 📊 Dataset Description
- **Source:** UCI Machine Learning Repository  
- **Observations:** 30,000 credit card clients  
- **Target Variable:**  
  - `Default` – Default payment next month  
  - `NoDefault` – No default  
- **Predictor Categories:**
  - Demographics: sex, education, marriage, age
  - Credit limit: `LIMIT_BAL`
  - Repayment history: `PAY_1` to `PAY_6`
  - Bill amounts: `BILL_AMT1` to `BILL_AMT6`
  - Payment amounts: `PAY_AMT1` to `PAY_AMT6`

---

## 🧹 Data Preprocessing
Key preprocessing steps included:
- Fixing incorrect header rows and cleaning column names
- Converting character variables to numeric
- Recoding categorical variables:
  - `SEX`: Male / Female
  - `EDUCATION`: GradSchool, University, HighSchool, Others
  - `MARRIAGE`: Married, Single, Others
- Converting repayment history variables into ordered factors
- Renaming the target variable to `y`
- Removing highly correlated bill amount variables to reduce multicollinearity
- Confirming no missing values in the dataset

---

## 📈 Exploratory Data Analysis (EDA)
Major findings from EDA:
- Credit limits are highly right-skewed, with many clients holding small limits
- Defaulting clients tend to have lower credit limits
- Age differences between default and non-default groups are minimal
- Repayment history (PAY variables) shows the strongest relationship with default
- Bill and payment amounts are highly correlated with significant outliers
- Class imbalance exists:
  - ~78% NoDefault
  - ~22% Default

---

## ⚖️ Class Imbalance Handling
To address class imbalance:
- Data was split using 70% training / 30% testing with stratification
- Up-sampling was applied to the training set to balance Default and NoDefault cases
- Models were trained and evaluated on both imbalanced and balanced datasets

---

## 🤖 Models Implemented
### Logistic Regression
- Used as a baseline and interpretable model
- Balanced training significantly improved sensitivity
- Key predictors include credit limit, repayment status, payment amounts, and demographic factors

### Decision Tree (CART)
- Highly interpretable structure
- Early splits dominated by recent repayment status (`PAY_1`)
- Balanced trees improved detection of default cases

### Random Forest
- Achieved the best overall accuracy and AUC
- Strong performance in both balanced and imbalanced settings
- Lower sensitivity compared to balanced logistic regression

---

## 📊 Model Performance Summary
**Imbalanced Data (Test Set):**
- Best Accuracy: Random Forest (~81.8%)
- Best Sensitivity: Random Forest
- Best Interpretability: Decision Tree

**Balanced Data (Test Set):**
- Best Sensitivity & Fairness: Logistic Regression
- Best AUC: Random Forest (~0.77–0.78)

**Final takeaway:**  
Balanced Logistic Regression offers the most reliable and fair default prediction, while Random Forest provides the strongest overall predictive power.

---

## 🛠 Tools & Libraries
- **Language:** R  
- **Key Packages:**
  - dplyr
  - ggplot2
  - caret
  - pROC
  - rpart, rpart.plot
  - randomForest
  - corrplot

---

## 🚀 Future Work
- Incorporate additional financial features such as income and spending patterns
- Explore advanced models (XGBoost, Gradient Boosting, Neural Networks)
- Apply SMOTE or hybrid resampling techniques
- Perform feature selection or dimensionality reduction
- Add explainability tools (SHAP values)
- Validate results using cross-validation or time-based splits

