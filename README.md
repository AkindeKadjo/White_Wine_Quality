# White_Wine_Quality


## Author: Akinde Kadjo

![image](https://user-images.githubusercontent.com/111167621/196629836-5b830b2b-4f4c-4cbe-8618-3f957fc4d9e0.png)


Image taken from [adrianysus.*com*](https://adrianysus.com/en/what-is-the-difference-between-chardonnay-pinot-grigio-and-sauvignon-blanc/)

## Introduction and Goals

A common saying state that beauty lies in the eyes of the beholder; well, this could be applied to some extent when it comes to gaging wine quality. Wine quality assessment is often regarded as somewhat subjective, although there are definitely metrics that wine connoisseur tends to agree on. According to [bkwine.com](https://www.bkwine.com/features/more/assessing-wine-quality-ageing-potential-wine-pursuit-perfectly-mature-wine/#:~:text=Most%20people%20who%20evaluate%20the,used%20quality%20criteria%20for%20wine.) the main indices are: **balance** (no individual parts should be overwhelming), **length** (the persistence of the taste), **intensity** (indicative of the concentration), **complexity** (reflects the aromas and flavors), **acids**, and **tannins** (bitter and astringent taste). Knowing how all of these indices contributes to the appraisal of wine quality, one would wonder if the chemical components could of a wine sample could help gage what its potential metric would be. For this project, the goal is to model wine quality based on physicochemical tests available from a set of white *vinho verde* wine samples, from the north of Portugal.

## Data Info
The provided datasets is that of the white *vinho verde* wine samples, from the north of Portugal. [Data Source](https://archive.ics.uci.edu/ml/datasets/wine+quality)


## Methods Used
The language used for this Project is Python in a Collaboratory environment.
Data cleaning protocol consisted of checking for duplicate (then removing them), checking for the presence of missing data, and fixing inconsistent data by removing significant outliers (data points outside of five time the standard deviation). Scikit libraries were used for machine learning. The nature of the target column, being the quality metrics, were both discrete and ordinal which allowed the pursuit of predicting those metrics using either a regression method or a classification method. Both avenues were explored. The methods of choice were RandomForestRegressor, XGBRegressor, RandomForestClassifier and XGBClassifier both with and without PCA. Tuning was applied as needed.


## Results and Interpretation

A glance at the data distribution shows us that is overwhelmingly composed of wine quality metrics #5, #6, and #7 with very few #3, #4, #8, and #9.

![image](https://user-images.githubusercontent.com/111167621/196871444-d4d6cc63-61e3-4e07-9dfb-cb67f111372a.png)

>
How do the metrics fare as a function of their chemical compositions? No clear trends could be drawn when it came to volatile acidity, citric acid, residual sugar, free sulfur dioxide. A somewhat of a positive correlation is observed with pH, sulphates and alcohol with few exceptions. On the other end, Fixed acidity, chlorides, total sulfur dioxide had a negative correlation with as well few exceptions.

![image](https://user-images.githubusercontent.com/111167621/196871614-4c9250a5-51a6-474d-84b9-17e84c53b238.png)

>
As stated above, the ordinality of our data set allowed for the prediction to be treated as a regression problem. The initial method used was Random Forest Regressor with resulted in a low R^2 of 0.3421 for the test data set and RMSE of 1 which indicated that the model would most likely be off by one metric #. Optimizing it slightly improved the R^2.  Random Forest Regressor with PCA and optimized Random Forest Regressor with PCA improved the R^2 to 0.3675. In an effort to get better prediction scores, XGBRegressor was used but at last it resulted in an even lower R^2 of 0.3164 for the test data set.

![image](https://user-images.githubusercontent.com/111167621/196875690-edf9dff6-cc32-4c50-aa34-97aafcdb283d.png)

>
The second option was to use classification methods to predict the wine quality metrics. The first trial with RandomForest Classifier without PCA resulted in an overall accuracy of 54% with 65% of the wine quality #6 are accurately predicted with the second best of 58% for wine quality #5. Here, the impact of the data imbalanced is clearly visible as all of the wine quality #3 and #9 were falsely predicted to be #6 and #7 respectively. Adding a balanced weight slightly improved the overall accuracy from 54% to 56%. RandomForest Classifier with PCA and XGBoost Classifier with PCA didn’t increase the overall accuracy.

![image](https://user-images.githubusercontent.com/111167621/196878808-f1bd84db-5bad-40cd-9bf5-7daa21a8a82f.png)


## Conclusion
Overall, with an accuracy of 56% we were able to predict white wine quality metrics from their physicochemical tests. Although the data received was from the white *vinho verde* wine samples, from the north of Portugal, it would be interesting to see how our predictions fares against other wine samples or if we would get an entirely different prediction from a much larger sample size.

### For further information
For any additional questions, please contact Akinde at akindeflo@gmail.com
