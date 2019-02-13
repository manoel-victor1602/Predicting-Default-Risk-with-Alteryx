# Predicting Default Risk with Alteryx
Using Alteryx Desifn to find out patterns in a bank's clients database to predict if a customer is creditworthy.

# 1- Data Understanding

- Project Timeline

First, we need to decide which of the variables in the dataset will stay and which will be removed based on the p-values and the correlation between the variables, then we need to decide how to impute the missing values in the Age-Years attribute, with the data cleaned, we need to build the models and verify which performed better in the validation set based on what the manager cares more, in this case accuracy, then with the model that performed better, score the data in “customers_to_score.xlsx”.

The data needed to inform those decisions are 2 different sets of data, 14 columns in “credit-data-training.xlsx”, the columns are: Credit-Application-Result, Account-Balance, Duration-of-Credit-Month, Payment-Status-of-Previous-Credit, Purpose, Credit-Amount, Value-Saving-Stocks, Length-of-current-employment, Instalment-per-cent, Most-valuable-available-asset, Type-of-apartment, No-of-Credits-at-this-Bank, Occupation, Age-Year, and the entire data in “customers_to_score.xlsx”.

# 2- Building the Training Set

<img src=”/field_summary_1.png”>
![alt text](http://url/to/field_summary_2.png)

I decided to remove the columns Concurrent-Credits, Guarantors, No-of-dependents, Foreign-Worker for their low variability, Duration-in-Current-address for having over 69% of missing values and Telephone for not giving any information about the customer’s creditworthiness. It was decided to impute the median in the missing values of the Age-Years attribute for being a whole number.

# 3- Training the Classification Models

1- Logistic Regression

![alt text](http://url/to/Coefficients.png)
