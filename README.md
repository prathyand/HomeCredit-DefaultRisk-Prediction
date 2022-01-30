# HomeCredit-DefaultRisk-Prediction
Predicting default risk probability of HomeCredit customers using different ML algorithms

## Abstract

Home Credit Default Risk is a project where we determine the credit worthiness of people that have applied for the loans. In previous phases, we had completed basic EDA, Feature Engineering and ran the baseline model for logistic regression and the hyperparameter tuning for XGBoost model.
In this Phase, we have significantly improved our project. We have updated the EDA, implemented robust Feature engineering for all dataset files, and did experimental analysis for hyper-parameter tuning for Logistic Regression, XGBoost and Random Forest Models. We conducted experiments using both original imbalanced data as well as resampled data. After comparison we found out that the XGBoost model with parameters: { learning_rate: 0.1, max_depth=5, min_child_weight=3 } was the best model, using the model performance criteria of Test AUC Score (0.7427).
For the deep learning Pytorch model, we used a feed-forward MLP with two hidden layers of 128 and 64 neurons each. We used a sigmoid activation function and SGD optimizer with cross entropy as loss function. The model achieved the test accuracy of 40%. The best Kaggle submission that we obtained was from XGBoost model with the Private Score 0.64788 and Public Score of 0.65231.

## Project Description
### Data Description
Home Credit is a non-banking financial institution, founded in 1997 in the Czech Republic. The company operates in 14 countries (including United States, Russia, Kazahstan, Belarus, China, India) and focuses on lending primarily to people with little or no credit history which will either not obtain loans or became victims of untrustworthly lenders. Home Credit group has over 29 million customers, total assests of 21 billions Euro, over 160 millions loans, with the majority in Asia and and almost half of them in China (as of 19-05-2018). While Home Credit is currently using various statistical and machine learning methods to make these predictions, they're challenging Kagglers to help them unlock the full potential of their data. Doing so will ensure that clients capable of repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower their clients to be successful.

There are 7 different sources of data:
  - **application_train/application_test:** the main training and testing data with information about each loan application at Home Credit. Every loan has its own row and is identified by the feature SK_ID_CURR. The training application data comes with the TARGET indicating 0: the loan was repaid or 1: the loan was not repaid. The target variable defines if the client had payment difficulties meaning he/she had late payment more than X days on at least one of the first Y installments of the loan. Such case is marked as 1 while other all other cases as 0.
  - **bureau:** data concerning client's previous credits from other financial institutions. Each previous credit has its own row in bureau, but one loan in the application data can have multiple previous credits.
  - **bureau_balance:** monthly data about the previous credits in bureau. Each row is one month of a previous credit, and a single previous credit can have multiple rows, one for each month of the credit length.
  - **previous_application:** previous applications for loans at Home Credit of clients who have loans in the application data. Each current loan in the application data can have multiple previous loans. Each previous application has one row and is identified by the feature SK_ID_PREV.
  - **POS_CASH_BALANCE::** monthly data about previous point of sale or cash loans clients have had with Home Credit. Each row is one month of a previous point of sale or cash loan, and a single previous loan can have many rows.
  - **credit_card_balance:** monthly data about previous credit cards clients have had with Home Credit. Each row is one month of a credit card balance, and a single credit card can have many rows.
  - **credit_card_balance:** payment history for previous loans at Home Credit. There is one row for every made payment and one row for every missed payment.
 
### Workflow
![alt text](https://github.com/prathyand/HomeCredit-DefaultRisk-Prediction/blob/main/images/pd.png)

### Data Leakage Control
We performed feature engineering on secondary datasets and merged with application train and application test. For feature selection from application train, we selected top 50 numeric features based on the correlation with target variable. All the numeric features as well as the engineered features were part of the final dataset.
We used pipelines to avoid the data leakage during preprocessing of numeric and categorical features. All the models were built with data pipeline + estimator as a single pipeline for Cross Validation purposes.

### Modelling Pipelines:
![alt text](https://github.com/prathyand/HomeCredit-DefaultRisk-Prediction/blob/main/images/mp.png)

### Results
![alt text](https://github.com/prathyand/HomeCredit-DefaultRisk-Prediction/blob/main/images/res.png)

In this phase, we have improved on the Phase 2 submission by improving our EDA and implementing 
additional feature engineering on all the secondary datasets. We also performed hyperparameter tuning on different models. We improved on the model evaluation criteria as accuracy was giving a false representation of the goodness of fit. We have used F1 score and AUC as our primary model evaluators. We also implemented the Pytorch Deep Learning model with 2 hidden layers. We also did Kaggle Submissions for the Random Forest, XGBoost and the Neural Network model.
