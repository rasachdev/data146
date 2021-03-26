# Midterm Corrections
## Setting it up
A. I imported all of the libraries that I would need in order to do this. 
B. Here is the DoKFold function:
```
def DoKFold(model, X, y, k, standardize=False, random_state=146):
    import numpy as np
    from sklearn.model_selection import KFold
    kf = KFold(n_splits=k, shuffle=True, random_state=random_state)
    
    if standardize:
        from sklearn.preprocessing import StandardScaler as SS
        ss = SS()
        
    train_scores = []
    test_scores = []
    
    train_mse = []
    test_mse = []
    
    for idxTrain, idxTest in kf.split(X):
        Xtrain = X[idxTrain, :]
        Xtest = X[idxTest, :]
        ytrain = y[idxTrain]
        ytest = y[idxTest]
        
        if standardize:
            Xtrain = ss.fit_transform(Xtrain)
            Xtest = ss.transform(Xtest)
            
        model.fit(Xtrain, ytrain)
        
        train_scores.append(model.score(Xtrain, ytrain))
        test_scores.append(model.score(Xtest, ytest))
        
        ytrain_pred = model.predict(Xtrain)
        ytest_pred = model.predict(Xtest)
        
        train_mse.append(np.mean((ytrain - ytrain_pred) ** 2))
        test_mse.append(np.mean((ytest - ytest_pred) ** 2))
        
    return train_scores, test_scores, train_mse, test_mse
```
C. I imported the California Housing data
D. I set my features as X, created a names object as X_names, and set up y as my target

## 15
In this question, I looked at the correlations between the 4 mulitple choice answers of MedInc, AveRooms, AveBedrms, and HouseAg. With this code:
```
Xcopy = X_df.copy()
Xcopy['y'] = y
Xcopy.corr()
```
The correlations were MedInc = 0.688075, AveRooms = 0.151948, AveBedrms = 0.046701, and HouseAg = 0.105623. And according to these correlations, the feature most strongly correlated with the target is MedInc. 

## 16
For this question, I looked at the correlations between the 4 mulitple choice answers of MedInc, AveRooms, AveBedrms, and HouseAg once the features were standardized. First I standardized the features and created a data frame with those standardized features. Then I looked at the correlations with the target that each had. 
```
Xtransf = ss.fit_transform(X)
Xtransf_df = pd.DataFrame(X, columns=X_names)
Xtransfy_df = Xtransf_df.copy()
Xtransfy_df['y'] = y
Xtransfy_df.corr()
```
After standardizing the features, none of the correlations between any of the variables changed. They all were the same from the previous question, #15. 

## 17
For this question, we performed a linear regression with the feature that was most correlated with the target in question 15. The feature was MedInc. 
```
np.round(np.corrcoef(X_df['MedInc'], y)[0][1]**2,2)
```
The coefficient of determination turned out to be 0.47

## 18
This question asks to perform a linear regression with a few requirements. The requirements are to standardize the data and perform a K-fold validation using: k=20, shuffle=True, random_state=146
```
k=20
train_scores, test_scores, train_mse, test_mse = DoKFold(LR(),X,y,k, True)

print(np.mean(train_scores), np.mean(test_scores))
print(np.mean(train_mse), np.mean(test_mse))
```
Looking at the R2 value on the test folds, the value for that, to 5 decimal places, is 0.60198.  

## 19
For this question, we looked a ridge regression using the same settings for K-fold validation as the previous question. I created objects to append my calculated mean values from my ridge training data and ridge testing data. I also created objects to append my calculated mean MSE values from my ridge training data and my ridge testing data. I looked at 101 equally spaced values between 20 and 30 for alpha. 
```
rid_a_range = np.linspace(20, 30, 101)

rid_tr = []
rid_te = []
rid_tr_mse = []
rid_te_mse = []

for a in rid_a_range:
    mdl = Ridge(alpha=a)
    train, test, train_mse, test_mse = DoKFold(mdl,X,y,k, True)
    
    rid_tr.append(np.mean(train))
    rid_te.append(np.mean(test))
    rid_tr_mse.append(np.mean(train_mse))
    rid_te_mse.append(np.mean(test_mse))

idx = np.argmax(rid_te)
print(rid_a_range[idx], rid_tr[idx], rid_te[idx], rid_tr_mse[idx], rid_te_mse[idx],)
```
Based on that, I was able to get a mean R2 value of the test folds of 0.60201, with the optimal value of alpha in that range. 

## 20
For this question, we looked a lasso regression using the same settings for K-fold validation as the previous two questions. I, once again, created objects to append my calculated mean values from my lasso training data and lasso testing data. I also created objects to append my calculated mean MSE values from my lasso training data and my lasso testing data. I looked at 101 equally spaced values between 0.001 and 0.003 for alpha. Essentially, it was almost the same work as the ridge regression. 
```
las_a_range = np.linspace(0.001, 0.003, 101)

las_tr = []
las_te = []
las_tr_mse = []
las_te_mse = []

for a in las_a_range:
    mdl = Lasso(alpha=a)
    train, test, train_mse, test_mse = DoKFold(mdl,X,y,k, True)
    
    las_tr.append(np.mean(train))
    las_te.append(np.mean(test))
    las_tr_mse.append(np.mean(train_mse))
    las_te_mse.append(np.mean(test_mse))

idx = np.argmax(las_te)
print(las_a_range[idx], las_tr[idx], las_te[idx], las_tr_mse[idx], las_te_mse[idx],)
```
Based on that, I was able to get a mean R2 value of the test folds of 0.60213, with the optimal value of alpha in that range.

## 21
This question is focused on correlations and coefficients. It asks which of the models estimates the smallest coefficient for the variable that is least correlated in terms of their absolute value. The variable that is least correlated is AveOccup. So with the linear, ridge, and lasso models, the absolute value of their coefficients are 0.03932626697814858, 0.03941257372893634, and 0.037618233645534585, respectively. And comparing all three of them, we can see that the lasso regression has the smallest coefficient for the AveOccup variable. 
```
print(X_names[5])
lin = LR(); rid=Ridge(alpha=25.8); las = Lasso(alpha=0.00186)
lin.fit(Xs,y); rid.fit(Xs,y); las.fit(Xs,y)
lin.coef_[5], rid.coef_[5], las.coef_[5]
```

## 22
Again we are looking at correlations and coefficients. But this question asks which of the models estimates the smallest coefficient for the variable that is most correlated in terms of their absolute value. The variable that is most correlated is MedInc. So with the linear, ridge, and lasso models, the absolute value of their coefficients are 0.8296193042804432, 0.8288892465527583, and 0.8200140807502062, respectively. And comparing all three of them, we can see that the lasso regression again has the smallest coefficient for the MedInc variable. 
```
print(X_names[0])
lin = LR(); rid=Ridge(alpha=25.8); las = Lasso(alpha=0.00186)
lin.fit(Xs,y); rid.fit(Xs,y); las.fit(Xs,y)
lin.coef_[0], rid.coef_[0], las.coef_[0] 
```

## 23
## 24 - If we had looked at MSE instead of R<sup>2</sup> when doing our Lasso regression (question 20), what would we have determined the optimal value for alpha to be? Enter your answer to 5 decimal places, for example: 0.12345
This is the corrected DoKFold function:
```

```

In order to answer the question  to find the optimal alpha value when looking at the Mean Squared Error(MSE) rather than the R<sup>2</sup> value in the Lasso Regression.
```
idx = np.argmin(las_te_mse)
print(las_a_range[idx], las_tr[idx], las_te[idx], las_tr_mse[idx], las_te_mse[idx],)
```
The optimal alpha value for the MSE in the Lasso Regression is 0.00186

There were a few reasons why I went wrong. The first was my DoKFold function. 
