#  The objective of this project is to predict if a customer is happy or not based on the answers they give to questions asked.

## Data Description:

* Y = target attribute (Y) with values indicating 0 (unhappy) and 1 (happy) customers
* X1 = my order was delivered on time
* X2 = contents of my order was as I expected
* X3 = I ordered everything I wanted to order
* X4 = I paid a good price for my order
* X5 = I am satisfied with my courier
* X6 = the app makes ordering easy for me

Attributes X1 to X6 indicate the responses for each question and have values from 1 to 5 where the smaller number indicates less and the higher number indicates more towards the answer.

## Conclusion of data exploration:

* The data is balanced
* There are no missing values
* There are outliers
* The data has the expected range
* There is no strong correlation between the features as well as the target variable
* X4 and X2 correlation with the target is almost zero
* X5 and X1 have good correlation and one is a direct consequence of the other
* Values of X1 that are equals to 3, 4 or 5 results in a target variable equals to 1
* Values of X5 that are equals to 4 or 5 results in a target variable equals to 1
* Values of X6 that are equals to 4 or 5 results in a target variable equals to 1

## Baseline model:


We only want to focus on the dissatisfied clients, so we can identify the problems here. So, we will aim for the metric that cares about the negatives outcomes 0.
For this, we will focus on the specificity.



The best score was achieved with data 'base_v6_X4.csv' with:
* Accuracy score: 72.73% 
* AUC ROC score: 71.67%
* F1 score: 76.13%  
* Specificity score: 60.00% 



## Results with the best model:
Models tested:
* Logistic Regression
* Random Forest
* XGBoost
* Support Vector Machine for classification
* Ridge Classifier

Best result so far:
The dataset is: base_v6_X4_X6.csv ( without features 4 and 6)
Model: SVC
The shape of the dataset is: (109, 5)
* Accuracy score: 72.73% 
* AUC ROC score: 73.33%
* F1 score: 72.73%  
* Specificity score: 80.00% 

## Conclusion

The dataset that gave us the best results was the one without:
* X4 = I paid a good price for my order
* X6 = the app makes ordering easy for me 

Data without the datapoints that represented the minority of the dataset gave us better results. They are not outliers per say, because they are in the expected range of values, but they are not the most common values.

This makes sense because,  X4 and X6 are things that are not directly related to the satisfaction of the customer, because if they were bad, people would not even order the food  with higher price than normal or use the app that is already difficult to use, so they are not the most important features to predict the satisfaction of the customer.

The emsembled models and the best estimator for this task, SVM, gave us the best results. This is due the capacity of SVC to find the best hyperplane to separate the data, and capture the non-linear relationships between the features and the target variable. 