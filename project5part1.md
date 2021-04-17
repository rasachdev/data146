# Project 5 - Part 1

## 1. Data Set Up
In order to work in the data there were a few steps I had to do first. After bringing the dataset into my workspace, I removed all the NaNs and changed all the values ot integers. These steps proved to be very helpful in order to get started on the regression I needed to do. 

## 2. Data Results on WealthC
First, I set the variable **wealthC** as my target. 

I performed a linear regression and computed the mean squared error, MSE. For the MSE, I got 0.44281. Then I standardized the features and again computed the MSE. With that step, I got the same MSE of 0.44281. When comparing the coefficients of the two models, the standardized coefficients is different from and smaller than the non-standardized set.

For my linear regression, I got a training score of 0.73084 and testing score of 0.73006. I also got a mean MSE trainging score of 0.44279 and a mean MSE testing score of 0.44375.

Next I ran a ridge regression on the dataset given. The results I got were an alpha value of 76.0 with a training score of 0.73584 and a testing score of 0.73505. Overall, there was a strong correlation between the features and targets as the R squared value was so close to 1. The ridge regression also shows an improvement in correlation from the linear regression. 

Then I ran a lasso regression. The results I got were an alpha value of 0.000263 with a trainging score of 0.73583 and a testing score of 0.73506. Again, like the ridge regession, the lasso regression also shows a very strong correlation between the features and targets from the data. Though a very very slight improvement, the score is virtually the same but I'd say the lasso regression performed the best for WealthC. 

## 3. Data Results on WealthI
The next step was changing my  target variable to **wealthI**. I did the same steps as the previous step. 
MSE:
MSE after standardization:
Coefficients:
Ridge Regression:
Lasso Regressoin:

## 4. Best Results from Data
