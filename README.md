# Predicting Default Risk with Alteryx
Using Alteryx Desifn to find out patterns in a bank's clients database to predict if a customer is creditworthy.

# 1- Data Understanding

- Project Timeline
First, we need to decide which of the variables in the dataset will stay and which will be removed based on the p-values and the correlation between the variables, then we need to decide how to impute the missing values in the Age-Years attribute, with the data cleaned, we need to build the models and verify which performed better in the validation set based on what the manager cares more, in this case accuracy, then with the model that performed better, score the data in “customers_to_score.xlsx”.

The data needed to inform those decisions are 2 different sets of data, 14 columns in “credit-data-training.xlsx”, the columns are: Credit-Application-Result, Account-Balance, Duration-of-Credit-Month, Payment-Status-of-Previous-Credit, Purpose, Credit-Amount, Value-Saving-Stocks, Length-of-current-employment, Instalment-per-cent, Most-valuable-available-asset, Type-of-apartment, No-of-Credits-at-this-Bank, Occupation, Age-Year, and the entire data in “customers_to_score.xlsx”.

# 2- Building the Training Set

![alt text](http://url/to/field_summary_1.png)
![alt text](http://url/to/field_summary_2.png)

I decided to remove the columns Concurrent-Credits, Guarantors, No-of-dependents, Foreign-Worker for their low variability, Duration-in-Current-address for having over 69% of missing values and Telephone for not giving any information about the customer’s creditworthiness. It was decided to impute the median in the missing values of the Age-Years attribute for being a whole number.

# 3- Training the Classification Models

1- Logistic Regression

Coefficients |                                            |
             | Estimate | Std. Error | Z-value | Pr(>|z|) |
-------------|----------|------------|---------|----------|
(Intercept)	 |-29.621.914 |	6,84E+02 |	-43.326|	1,00E-05	*** | 
Account.BalanceSome Balance |	-16.053.228 |	3,07E+02 |-52.344 |	1.65e-07	*** |
Payment.Status.of.Previous.CreditPaid Up |	0.2360857 |	2,98E+02 |	0.7930 |	0.42775|	 
Payment.Status.of.Previous.CreditSome Problems |	12.154.514 |	5,15E+02 |	23.595 |	0.0183	* |
PurposeNew car |	-16.993.164 |	6,14E+02 |	-27.668 |	0.00566	** |
PurposeOther |	-0.3257637 |	8,18E+02 |	-0.3983 |	0.69042	 |
PurposeUsed car |	-0.7645820 |	4,00E+02 |	-19.096 |	0.05618	|.
Credit.Amount |	0.0001704 |	5,73E-02 |	29.716 |	0.00296	** |
Length.of.current.employment4-7 yrs |	0.3127022 |	4,59E+02 |	0.6817 |	0.49545	 |
Length.of.current.employment< 1yr |	0.8125785 |	3,87E+02 |	20.973 |	0.03596	* |
Instalment.per.cent |	0.3016731 |	1,35E+02 |	22.340 |	0.02549	* |
Most.valuable.available.asset |	0.2650267 |	1,43E+02 |	18.599 |	0.06289 |	.
Significance codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 |
