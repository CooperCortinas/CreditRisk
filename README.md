# Credit Risk Analysis

## Overview
This project analyzes customer credit risk using machine learning techniques. The dataset includes customer demographics and payment history, and the goal is to classify customers into high or low credit risk categories.

## Data Sources
- **customer_data.csv**: Contains demographic and categorical attributes of customers.
- **payment_data.csv**: Contains customers' payment history and account details.

## Methodology
The analysis follows these steps:
1. **Data Preprocessing**: Merging datasets, handling missing values, and feature engineering.
2. **Feature Engineering**: Creating financial indicators such as credit utilization ratio and debt burden ratio.
3. **Model Training**: Using Logistic Regression, Decision Trees, and XGBoost for classification.
4. **Evaluation**: Using accuracy, precision, recall, and AUC-ROC to assess model performance.
5. **Feature Importance Analysis**: Using SHAP values and XGBoost feature importance scores.
6. **Hypothesis Testing**: Testing to see if differences in model performances are statistically significant.

## Key Findings
- **Best Model**: XGBoost Model using demographic/categorical attributes and engineered features (Credit Utilization Ratio, Overdue Payment Frequency, Debt Burden Ratio)
- **Top Features Influencing Risk**: Overdue Payment Frequency, fea_4 (Encoded Variable), fea_1 (Encoded Variable)
- **Significance of Features**: T-test between means for Accuracy and ROC-AUC for models using no categorical variables, and including them

## Model Performance: Engineered Features and Categorical Variables

| Model               | Accuracy | Precision | Recall | ROC-AUC |
|---------------------|----------|-----------|--------|---------|
| Logistic Regression | 0.8318 | 0.5333 | 0.0045 | 0.6685 |
| Decision Tree      | 0.9791 | 0.9407 | 0.9360 | 0.9619 |
| XGBoost            | 0.9874 | 0.9887 | 0.9360 | 0.9896 |

## Statistical Test for Feature Selection Impact

- **Null Hypothesis**: Categorical variable addition has no effect on the accuracy and ROC-AUC of the models.
- **Alternative Hypothesis**: Categorical variable addition has an effect on the accuracy and ROC-AUC of the models.
  
| Metric  | p-value |
|---------|---------|
| Accuracy | 0.1162 |
| ROC-AUC  | 0.0746 |

- **p-value**: The probability of observing the given results (or more extreme ones) if the null hypothesis is true.
- **Small p-value**: (typically < 0.05) suggests that the observed effect is unlikely due to chance, leading to rejection of the null hypothesis.
- **Large p-value**: (> 0.05) suggests that the observed effect could have occurred by chance, meaning there is not enough evidence to reject the null hypothesis.

**Interpretation**: Since p > 0.05, we fail to reject the null hypothesis, meaning there is no strong statistical evidence that adding categorical variables significantly impacts model accuracy.

However, since ROC-AUC p = 0.0746 is close to 0.05, there may be a weak effect on model discrimination at a 90% confidence level.

## Usage
To run the analysis, execute the Jupyter Notebook `CreditRisk.ipynb` in a Python environment with required dependencies installed.
