# Customer Churn Prediction Project

## Introduction
Customer attrition, also known as customer churn, customer turnover, or customer defection, is the loss of clients or customers. In this project, we assume that "customer churn is bad" and "customer retention is good."

## Abstract
This documentation takes a unique approach to a well-known churn dataset, addressing the challenge that the dataset may lack the right features for deploying even the best predictive models. This README will cover the problem statement, data preparation steps, feature analysis, visualizations, and select Python code from various Scikit-learn classification models used for predicting customer churn. Most importantly, it demonstrates how adjusting the decision threshold probability along the precision-recall curve can help identify churn cases with confidence, leading to effective retention actions.

For detailed code and analysis, refer to the Jupyter notebook on [GitHub](https://github.com/hyounas865/Enhancing_customer_retention_telco_custom).

## Business Objective
A telecommunications company ("TelCo") is facing a significant customer churn rate of nearly 27%, which could potentially be disastrous for the company. Using the IBM Cognos Telco Customer Churn simulated dataset containing labeled churn for 7,043 customers, the objectives are:

- Develop a predictive model to classify customer churn risk.
- Explain the relative influence of each predictor on the model’s predictions.
- Suggest potential approaches to reduce customer churn.

This is a binary classification problem where the target variable is 1 (churn) or 0 (retain). The ROC AUC metric is used to optimize estimators, as it measures both true positive and false positive rates, providing confidence in positive class predictions.

## Customer Churn Raw Data
The dataset includes 33 columns. Here’s a brief overview:

- **Customer**: Unique customerID for 7,043 customers with tenure from 0 to 72 months.
- **Demographic**: Customer demographic information.
- **Geographic**: Location data down to geographic coordinates.
- **Service**: Billable services and streaming indicators.
- **Billing**: Contract type, billing configuration, and charges.
- **Churn**: Churn value (target), Churn Reason, and internal metrics like Churn Score and Customer Lifetime Value.

The dataset initially had 23 columns in a Kaggle competition but was expanded to 33 columns for deeper insights, though the added geographic fields did not significantly improve the analysis.

## Data Preparation
Data preparation involved creating six functions and using FunctionTransformer in a scikit-learn pipeline. Key features created include:

- **Payment Method Automated**: A binary feature indicating automated payment methods.
- **Product Profile**: Columns delineating core and add-on services.
- **Customer Charge Index**: Measures relative pricing of each customer compared to standard prices.

The data was split into 80% training and 20% test sets to avoid data leakage.

## Customer Churn Feature Analysis
Basic insights from the data include:

- **Churn Rate Insights**: Lower churn rates for customers with partners, dependents, not senior citizens, and those who stream content.
- **Contract Insights**: Month-to-month (M-T-M) contracts have a high churn rate (43%) compared to term-based contracts.
- **Product Insights**: Internet Fiber on M-T-M contracts has the highest churn rate. Customers with M-T-M contracts are more price-sensitive.

## Predicting Customer Churn
Four classification models were trained on the training data: Decision Tree, Logistic Regression, Random Forest, and XGBoost. GridSearchCV was used for parameter tuning. The XGBoost model, with an AUC of 0.79, was chosen due to its superior performance.

### Model Performance
- **Recall**: 83%
- **Precision**: 54%
- **Key Features**: 1-year and 2-year contracts, Internet Fiber products, and Dependents.

## Moving the Decision Threshold
The model’s default threshold of 0.5 churn probability was adjusted to improve precision. The recommended thresholds are:

- **High Precision (DT=0.9–1.0)**: 84% Precision / 18% Recall
- **Medium Precision (DT=0.8–0.9)**: 71% Precision / 26% Recall
- **Low Precision (DT=0.7–0.8)**: 49% Precision / 19% Recall

### Recommended Actions
- **High Precision**: Proactive outreach with discounts or free services.
- **Medium Precision**: Empower customer service agents for retention.
- **Low Precision**: General retention communications or watch lists.

## Conclusion
This project demonstrates the importance of adjusting the decision threshold to balance precision and recall in customer churn prediction. By strategically targeting retention efforts, TelCo can reduce churn more effectively.

For detailed analysis, visualizations, and code, please refer to the Jupyter notebook on [GitHub](https://github.com/hyounas865/Enhancing_customer_retention_telco_custom).
