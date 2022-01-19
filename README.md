# Predicting Recidivism :Overview
* Full project code and explanation is available [here](https://github.com/grantjw/predict_recidivism_proj3/blob/main/pred_recid.pdf). You can also download the "pred_recid.html" file or use the [Rmarkdown file](https://github.com/grantjw/predict_recidivism_proj3/blob/main/pred_recid.Rmd) to try the code yourself.

## Project Goal
* Predict which criminal defendants are likely to recidivate using supervised machine learning techniques. 

## Data Cleaning
* Made dummy varibales for different races
* drop variables irrelevant to the training model such as "id" 
* change outcome varible to factor
* create a matrix of predictor variables 
* boostrap the data for re-sampling 

## Model Building
With a 80/20 split, I tried three different models:
### * Elastic Net: Used optimal lambda within one standard deviation of the minimum lambda. 
![alt_text](https://github.com/grantjw/predict_recidivism_proj3/blob/main/loglamb.PNG) 
* Random Forests with Out of Bag error using grid search. 
![alt_text](https://github.com/grantjw/predict_recidivism_proj3/blob/main/OOB.PNG)
* Gradient Boosted Trees with Number of trees vs. cv.error using grid search. 
![alt_text](https://github.com/grantjw/predict_recidivism_proj3/blob/main/n.trees.PNG)

## Metric
* In choosing our metric, we deemded that the alogrithm’s priority should be to predict “recidivate” for only those who actually recidivates. We hope to reduce “false positives” while increasing “True Positives.” In other words, we ask “for what proportion does the algorithm say it will recidivate correctly”? Precision and FPR are seen as more important as they are more related to costs to defendants. The algorithm at least should not put defendants in jail who actually would not recidivate. In contrast, metrics such as FNR and Recall are more related to costs to society, as societies do not want defedants to recidivate in society. Although costs to society is important as well. The cost to defedants is argubly more important in our perspective.

## Model Performance 
Out of the three models Random Forests performed best on the precision metric. 
Elastic Net: **“67.67%”**, Random Forests: **“69.50%”**, Gradient Boosted Trees: **“68.55%.”**

## Results/Discussions
* Used Random Forest as final model and achieved the highest test set (held out dataset that only the professor has) predictive performance in class with **72% precision**.
* The reasoning behind choosing random forest as our model of choice is explained in the actual code. 
* Using race as a predictor variable can be controversial.
* Things like calibration plots are needed to further assess the "mathematical incompatbility" of fairness notions. 

## Data
* historical data set of 6,000 criminal defendants from Broward County, Florida

## Code Used 
R Version: 1.3.1093 

