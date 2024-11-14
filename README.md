# Customer Churn Prediction

This project aims to predict customer churn (whether a customer will leave) based on various features such as account details, customer satisfaction, and demographics. The dataset used contains customer information, and the task is to build machine learning models to predict the "Exited" column, which indicates if a customer has left.  
The dataset used can be found here: https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn

## Dataset Overview

The dataset contains the following columns:
- `RowNumber`: Row index
- `Surname`: Customer surname
- `CustomerId`: Unique identifier for each customer
- `Gender`: Gender of the customer
- `NumOfProducts`: Number of products used by the customer
- `HasCrCard`: Whether the customer has a credit card
- `IsActiveMember`: Whether the customer is an active member
- `Exited`: Target variable (whether the customer left the service)
- `Complain`: Whether the customer has filed a complaint
- `Satisfaction Score`: A score indicating the customer's satisfaction
- `Card Type`: The type of card the customer holds (e.g., platinum, diamond)
- `Geography`: The country where the customer is located

## Data Preprocessing

1. **Data Cleaning**:
    - Dropped unnecessary columns (`RowNumber`, `Surname`, `CustomerId`).
    - Converted specific columns to categorical data types (`Gender`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `Exited`, `Complain`, `Satisfaction Score`, `Card Type`, `Geography`).

2. **Descriptive Statistics**:
    - Generated descriptive statistics for numeric columns.
    - Displayed value counts for non-numeric columns.

3. **Dummy Variables**:
    - Converted categorical columns (`Gender`, `Geography`, `Card Type`) into dummy variables for modeling.

4. **Feature and Target Arrays**:
    - Defined `X` (features) by dropping the target variable (`Exited`).
    - Defined `y` (target) as the `Exited` column.

## Model Training and Evaluation

The following models were trained and evaluated:
- **Logistic Regression**
- **K-Nearest Neighbors (KNN)**
- **Decision Tree**

### Cross-Validation

We performed 10-fold cross-validation on each model and plotted the results using boxplots. Initial cross-validation scores ranged from 0.98 to 1.0, which indicated potential overfitting.

### Accuracy Evaluation

We then trained each model on the training data and evaluated them on the test data. Initial accuracy scores were exceptionally high, which pointed to a potential issue with the dataset, specifically the strong correlation between the `Complain` and `Exited` columns.

### Investigating Correlation

The correlation between the `Exited` and `Complain` columns was found to be 0.9956, suggesting that almost all customers who complained also exited, which made the models overly accurate.

### Re-evaluation Without 'Complain' Column

To address the issue, we removed the `Complain` column and re-trained the models. The new cross-validation scores ranged from 0.77 to 0.83, which was a significant decrease compared to the initial results.

## Conclusion

- The initial high accuracy scores were primarily driven by the high correlation between the `Complain` and `Exited` columns.
- After removing the `Complain` feature, the accuracy decreased to more reasonable levels, though the models still performed decently.
- The results suggest that further tuning and feature engineering may be needed to improve the model’s predictive power without overfitting.
