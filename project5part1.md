# Project 5 - Part 1

## 1. Data Set Up
In order to work in the data there were a few steps I had to do first. After bringing the dataset into my workspace, I removed all the NaNs and changed all the values ot integers. These steps proved to be very helpful in order to get started on the regression I needed to do. 
```
pns = pd.read_csv('persons.csv')

check_nan = pns['age'].isnull().values.any()
pns.dropna(inplace=True)

pns['age'] = pns['age'].astype(int)
pns['edu'] = pns['edu'].astype(int)
```

## 2. Data Results on WealthC
First, I set the variable **wealthC** as my target. 
```
X = pns.drop(["wealthC", "wealthI"], axis=1)
y = pns.wealthC
```
I performed a linear regression and computed the mean squared error, MSE. For the MSE, I got 0.44281. Then I standardized the features and again computed the MSE. With that step, I got the same MSE of 0.44296. When comparing the coefficients of the two models, the standardized coefficients is different from and smaller than the non-standardized set.

For my linear regression, I got a training score of 0.73084 and testing score of 0.73006. I also got a mean MSE trainging score of 0.44279 and a mean MSE testing score of 0.44375. After standardizing the data, I got a training score of 0.73072 and testing score of 0.73002. Copared to the non-standardized set, these are slightly lower yet a very insignificant different. The standardized mean MSE trainging score was 0.44281 and the mean MSE testing score was 0.44369. Again, very close and different but still extremely insignificant. 

Next I ran a ridge regression on the dataset given. The results I got were an alpha value of 72.6514 with a training score of 0.73584 and a testing score of 0.73505. Overall, there was a strong correlation between the features and targets as the R squared value was so close to 1. The ridge regression also shows an improvement in correlation from the linear regression I previously performed. 

Then I ran a lasso regression. The results I got were an alpha value of 0.0002633 with a trainging score of 0.73583 and a testing score of 0.73506. Again, like the ridge regession, the lasso regression also shows a very strong correlation between the features and targets from the data. Though a very very slight improvement, the score is virtually the same as the ridge regression but I'd say the lasso regression performed the best for WealthC. 

## 3. Data Results on WealthI
The next step was doing all my previos steps on a different variable. I used the variable to **wealthI** as my target.
```
X = pns.drop(["wealthC", "wealthI"], axis=1)
y = pns.wealthI
```
I performed a linear regression and computed the mean squared error, MSE. For the MSE, I got 1750276834.9304798. Then I standardized the features and again computed the MSE. With that step, I got the same MSE of 1750287416.4378211. These are such large numbers which was a bit weird to get and do not know exactly what went wrong or what was going on. When comparing the coefficients of the two models, the standardized coefficients is different from and bigger than the non-standardized set.

For my linear regression, I got a training score of 0.73084 and testing score of 0.73006. I also got a mean MSE trainging score of 0.44279 and a mean MSE testing score of 0.44375. After standardizing the data, I got a training score of 0.73072 and testing score of 0.73002. Copared to the non-standardized set, these are slightly lower yet a very insignificant different. The standardized mean MSE trainging score was 0.44281 and the mean MSE testing score was 0.44369. Again, very close and different but still extremely insignificant.

## 4. Best Results from Data
