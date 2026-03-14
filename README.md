# Loan-Approval-Prediction-Model
- April 29th 2024
- MTH 2151 - Statistical Modeling
- Belmont University
- Author: Numa Rahman

### Dataset URL: 
Training Data: https://github.com/shrikant-temburwar/Loan-Prediction-Dataset/blob/master/train.csv

Testing Data: https://github.com/shrikant-temburwar/Loan-Prediction-Dataset/blob/master/test.csv


### Preprocessing & Cleaning: 
I extracted two tables from github and turned them into pandas dataframes. I concatenated the two dataframes so I could have more data overall. Most of the variables were categorical, so I mapped the categorical variables to numerical values to make them compatible with modeling tasks. I also completed a hot encoding task by creating a dummy variable for a categorical feature. I dropped any unnecessary variables and dropped all Nans from the dataset. I created a histogram of LoanAmount prior to the quantitative prediction to see the distribution of values. I did the same with LoanStatus prior to the qualitative prediction.

### Prediction 1: 
I made a logistic regression model to predict whether an applicant’s loan would be approved or not based on the column ‘LoanStatus’. Based on this summary, the 'Credit_History', 'Property_Area_Rural', and 'Property_Area_Urban' seemed to show the most significance (p-value < 0.05). Credit history, which signifies if an applicant's credit history meets the guidelines to get a loan, has a coefficient of 3.3755 showing that it positively impacts loan approval. Applicants from rural areas have a high negative coefficient. This suggests a lower probability of loan approval compared to other property locations. Applicants from urban areas also have a high negative coefficient, suggesting a lower likelihood of loan approval. The model, overall, did a good job of predicting the true values of loan approval with a sensitivity of 1. However, it over-predicted loan approval over loan denial. The specificity of .36 means the model is not performing well in identifying negative instances. This means the model tends to favor predicting "yes" for loan status. The accuracy score of 80% suggests that the model is performing well overall, but this score might be from the influence of a high sensitivity and low specificity. In conclusion, accuracy score is useful but it is important to consider other metrics to gain a full understanding of the model's performance. 

### Prediction 2: 
I made a regression tree to predict the loan amount an applicant would receive given their loan was approved. Before modeling, I made a histogram of target distribution values to get an understanding of where most of the values lie. The model achieved an RMSE score of 98.143 which means it was about $9.91 away from the actual loan amounts. I then made a decision tree and it performed terribly. All of the leaves had significantly high squared errors indicating the model’s struggle to predict loan amount correctly. Using the decision tree, I found that ApplicantIncome and CoapplicantIncome to be the most useful features in the model.

### Tuning & Validation: 
I used cross validation on my logistic regression model to see if it could get better results to increase the specificity. The cross validation technique performed worse than the original model with a score of 25%. This makes me believe the model may be overfitting to the validation set, so it performs poorly with unseen data. I made a feature importance graph with my decision tree to determine which features had the most significance. The graph showed Married, ApplicantIncome, and CoapplicantIncome to be the most important predictors. I performed forward feature selection to search for the top performing variables, and all of the predictors were chosen. I made an ROC curve for the logistic regression model to determine the best possible threshold for modeling and tuning. I also tuned the predicted probabilities of the logistic regression model into labels based on a threshold of 0.55 to achieve best model results.
