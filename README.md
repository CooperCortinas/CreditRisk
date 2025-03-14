# Credit Risk Analysis

## Overview
This project analyzes customer credit risk using machine learning techniques. The dataset includes customer demographics and payment history, and the goal is to classify customers into **high** or **low** credit risk categories.

## Data Sources
- **`customer_data.csv`** – Contains demographic and categorical attributes of customers.  
- **`payment_data.csv`** – Contains customers' payment history and account details.  

---

## Methodology
1. **Data Preprocessing** – Merging datasets, handling missing values, and feature engineering.  
2. **Feature Engineering** – Creating financial indicators such as:  
   - **Credit Utilization Ratio**  
   - **Overdue Payment Frequency**  
   - **Debt Burden Ratio**  
3. **Model Training** – Using **Logistic Regression, Decision Trees, and XGBoost** for classification.  
4. **Evaluation** – Assessing model performance using **Accuracy, Precision, Recall, and ROC-AUC**.  
5. **Feature Importance Analysis** – Using **SHAP values** and **XGBoost feature importance scores**.  
6. **Hypothesis Testing** – Testing whether model performance differences are **statistically significant**.  

---

## Engineered Features

- ### **Credit Utilization Ratio**  
The percentage of available credit that a customer is currently using:  

**Credit Utilization Ratio** = (Current Balance) / (Credit Limit)  

Where:  
- **Current Balance** = `new_balance`  
- **Credit Limit** = `prod_limit`  
<br><br>

- ### **Overdue Payment Frequency**  
The proportion of overdue payments relative to normal payments:  

**Overdue Payment Frequency** = (OVD_t1 + OVD_t2 + OVD_t3) / (pay_normal + 1)  

Where:  
- **OVD_t1, OVD_t2, OVD_t3** – Number of times overdue (Type 1, Type 2, Type 3)  
- **pay_normal** – Number of normal (on-time) payments  
- **`+1`** is added to avoid division by zero.  
<br><br>

- ### **Debt Burden Ratio**  
The proportion of debt relative to income:  

**Debt Burden Ratio** = (Current Balance) / (Income Proxy Variable)  

Where:  
- **Current Balance** = `new_balance`  
- **Income Proxy Variable** = `fea_10`  

<br><br>
## Key Findings
- **Best Model** – **XGBoost**, trained with **demographic/categorical attributes** and **engineered features.**  
- **Top Features Influencing Risk:**  
  1. **Overdue Payment Frequency**  
  2. **fea_4 (Encoded Variable)**  
  3. **fea_1 (Encoded Variable)**  
- **Significance of Features** – A **T-test** was conducted to compare **Accuracy** and **ROC-AUC** between models with and without categorical variables.  

---

## Model Performance: Engineered Features & Categorical Variables

| Model               | Accuracy | Precision | Recall | ROC-AUC |
|---------------------|----------|-----------|--------|---------|
| **Logistic Regression** | 0.8318 | 0.5333 | 0.0045 | 0.6685 |
| **Decision Tree**      | 0.9791 | 0.9407 | 0.9360 | 0.9619 |
| **XGBoost**        | **0.9874** | **0.9887** | **0.9360** | **0.9896** |

---

## Hypothesis Testing: Feature Selection Impact  

### **Null Hypothesis (H₀)**  
Adding categorical variables **does not significantly impact** model accuracy and ROC-AUC.  

### **Alternative Hypothesis (H₁)**  
Adding categorical variables **does impact** model accuracy and ROC-AUC.  

| Metric  | p-value |
|---------|---------|
| **Accuracy** | 0.1162 |
| **ROC-AUC**  | 0.0746 |

### **Interpretation:**  
- A **p-value** represents the probability of observing the given results **if the null hypothesis were true.**  
- Since **p > 0.05**, we **fail to reject** the null hypothesis. This means:  
  - There is **no strong statistical evidence** that adding categorical variables significantly impacts **accuracy**.  
  - However, since **ROC-AUC p = 0.0746** is **close to 0.05**, there may be **a weak effect on model discrimination** at a **90% confidence level.**  

---

## Installation
Clone the repository and install dependencies using:  
```bash
pip install -r requirements.txt


## Usage
To run the analysis, execute the Jupyter Notebook `CreditRisk.ipynb` in a Python environment with required dependencies installed.
