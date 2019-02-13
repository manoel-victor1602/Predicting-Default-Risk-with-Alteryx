# Predicting Default Risk with Alteryx
Using Alteryx Desifn to find out patterns in a bank's clients database to predict if a customer is creditworthy.

# 1- Data Understanding

First, we need to decide which of the variables in the dataset will stay and which will be removed based on the p-values and the correlation between the variables, then we need to decide how to impute the missing values in the Age-Years attribute, with the data cleaned, we need to build the models and verify which performed better in the validation set based on what the manager cares more, in this case accuracy, then with the model that performed better, score the data in “customers_to_score.xlsx”.

The data needed to inform those decisions are 2 different sets of data, 14 columns in “credit-data-training.xlsx”, the columns are: Credit-Application-Result, Account-Balance, Duration-of-Credit-Month, Payment-Status-of-Previous-Credit, Purpose, Credit-Amount, Value-Saving-Stocks, Length-of-current-employment, Instalment-per-cent, Most-valuable-available-asset, Type-of-apartment, No-of-Credits-at-this-Bank, Occupation, Age-Year, and the entire data in “customers_to_score.xlsx”.

# 2- Building the Training Set

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/field_summary_1.png">
<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/field_summary_2.png">

I decided to remove the columns Concurrent-Credits, Guarantors, No-of-dependents, Foreign-Worker for their low variability, Duration-in-Current-address for having over 69% of missing values and Telephone for not giving any information about the customer’s creditworthiness. It was decided to impute the median in the missing values of the Age-Years attribute for being a whole number.

# 3- Training the Classification Models

- 1. Logistic Regression

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/Coefficients.png">

The most important variables according to the Logistic Regression method are Account Balance, Payment Status of Previous Credit, Purpose, Credit Amount, Length of current employment, Installment per cent and Most valuable available asset.

The Logistic Regression Model achieved an overall accuracy of 76%. The model is bit biased to predict that the customer is creditworthy, comparing to the other models, it shows the best Accuracy for the Non-Creditworthy customers.

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/CM of LR Model.png">

- 2. Decision Tree

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/feature importance DT.png">

The most important variables according to the model are Account Balance, Duration of Credit Month and Value Savings Stocks.

The Decision Tree model achieved an overall accuracy of 74.67% in the validation set, comparing to the other model, this is the one with the less accurate. This model again shows to be biased to predict that the customer is creditworthy.

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/CM of DT Model.png">

- 3. Random Forest

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/Feature Importance RF.png">

Differently of the results of the single Decision Tree model, the Random Forest approach reached that the three most important variables are Credit Amount, Duration of Credit Month and Account Balance.

The model achieved an overall accuracy of 78.67% and it is the one chosen be used in the test set.

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/CM of RF Model.png">

- 4. Boosted Model

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/Variable Importance Boosted.png">

The Boosted model approach reached 5 most important variables that are Account Balance, Credit Amouont, Payment Status of Previous Credit, Payment Status of Previous Credit, Duration of Credit Month and Purpose.

The Boosted Model achieved an overall accuracy of 78.67% on the validation set, its Accuracy to predict Creditworthy customers is the highest achieved by all 4 models, however its Accuracy to predict Non Creditworthy customers is the worst, it means the model is biased to predict that the customer is creditworthy.

<img src="https://github.com/manoel-victor1602/Predicting-Default-Risk-with-Alteryx/blob/master/CM of Boosted.png">

# 4- Conclusion

I chose to use the Random Forest Model because it achieved the highest overall accuracy along with the Boosted Model, between these two, the Random Forest Model outperformed the Boosted Model in the Non-Creditworthy accuracy. With high values in the False Positive Rate in the ROC curve, the Random Forest performed slightly better than the Boosted, even though with the True Positive Rate being less than 0.5 it shows the worst results. As discussed before the Boosted model is biased to predict that the customer is Creditworthy, so analyzing these insights I opted for choosing the Random Forest Model. 

According to the Random Forest Model, there are 403 out of the 500 customers that are Creditworthy.
