# Midterm Corrections

## 24 - If we had looked at MSE instead of R2 when doing our Lasso regression (question 20), what would we have determined the optimal value for alpha to be? Enter your answer to 5 decimal places, for example: 0.12345
This is the corrected DoKFold function:
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

In order to answer the question  to find the optimal alpha value when looking at the Mean Squared Error(MSE) rather than the R<sup>2</sup> value in the Lasso Regression.
```
idx = np.argmin(las_te_mse)
print(las_a_range[idx], las_tr[idx], las_te[idx], las_tr_mse[idx], las_te_mse[idx],)
```
The optimal alpha value for the 
