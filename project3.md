# Project 3

## 1. 
For the Charleston Asking Price dataset, the features were beds, baths, and area is square feet and the target was the asking price. The linear regression model's training score was 0.019 and testing score was -0.013. The number of folds I put was 10. The linear regression model performs poorly because the R-Squared values are just so low and far from 1. The model poorly predicts the training and testing data. When I increase the folds, the testing score or external validity gets much lower. 

## 2.
With standardizing the features, the linear regression model's training score was 0.019 and testing score was -0.019. The number of folds I put was 10. The scores are basically the same as the previous question's scores. The testing score was a bit lower. The model still performs poorly. And again, with increasing the folds to higher number also decreases the testing score. 

## 3.
With  standardized data in the ridge regression model, the training score was 0.019 and testing score was 0.012 with 10 folds. The training score was the same as the previous question's score. But the model's testing score was imporved rather significantly, performing better to external data. Overall though, the model still performs poorly. When I increase the number of folds, the testing score gets lower.

## 4.
For the Charleston Actual Price dataset, I created 3 the same previous 3 models just with the new data. 

The linear regression model's training score was 0.004 and testing score was -0.029 with 10 folds. With standardizing the features, the linear regression model's training score was 0.004 and testing score was -0.025, with 10 folds. With standardized data in the ridge regression model, the training score was 0.004 and testing score was -0.009, with 10 folds.

In comparison to the Charleston Asking Price dataset, the Charleston Actual Price dataset less of the training data is explained by the model because 0.004 is less than 0.019. The training and testing scores are low so the model's aren't explaining much of the data. 

## 5.
For the Charleston Actual Price dataset, I added the zip code variables to the data and created 3 the same previous 3 models with the new data. The linear regression model's training score was 0.339 and testing score was 0.248 with 10 folds. With standardizing the features, the linear regression model's training score was 0.339 and testing score was -37102697289516817842176.000, with 10 folds. With standardized data in the ridge regression model, the training score was 0.334 and testing score was 0.275, with 10 folds.  

Similarly, for the Charleston Asking Price dataset, I added the zip code variables to the data and created 3 the same previous 3 models with the new data. The linear regression model's training score was 0.281 and testing score was 0.246 with 10 folds. With standardizing the features, the linear regression model's training score was 0.281 and testing score was 0.209, with 10 folds. With standardized data in the ridge regression model, the training score was 0.280 and testing score was 0.254, with 10 folds.

By adding the zip codes into each of the dataset's features, I was able to get betting training and testing scores. More the data was explained by the results proving to be more useful rather than just using beds, bath, and square feet. In comparison to the non-zip code data, the models with zip codes explain a more about of the data significatly. It is clearly seen by looking at the training and testing data.

## 6.
The model that produced the best results and did a better job with predicting was the standardized features linear regression model with zip codes. The data resulted in the highest training and testing data out of all the models or even known as the internal and external validity. But with the training and testing scores being so low, the model is underfit and is not perfect. A perfect model would have scores of 1, which only seems possible in an ideal world. But it's definitely better than the data that does not have the zip codes. If I were working for Zillow as their chief data scientist, I would recommend adding different data about the homes and neighborhoods. Things about the house like the year is was built and the number of days its been on the market could be added. Also things about the neighborhood like how many types of schools are in proximity to it and the number of different 'amenities' like community pools or tennis courts. Just beds, baths, and area isn't sufficient. 
