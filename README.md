# Credit-Card-Fraud-Detection
Identify fraudulent credit card transactions using Tree-based methods

## Introduction
This notebook evaluates input variables which are the result of a PCA transformation of transactions (privacy concerns) that occurred in two days. The focus is to use various predictive models to assess how accurate they are in detecting whether a transaction is a normal payment or a fraud. 
The five models are:
1. Logistic Regression
2. Decision Tree
3. Bagged Trees
4. Random Forest
5. Boosted Trees

Since the goal is to compare 5 models, and see which gives the best performance, evaluation is performed using the same holdout set.
Also, the dataset is highly unbalanced due to which accuracy is not a good metric to use here. Therefore, F1-score is used for hyperparameter selection for all models. ROC curve and AUC score is also used because it is a good method to use when comparing multiple classification algorithms. 
The original dataset contains roughly 280K observations. The data I have used is simplified down to roughly 3000 observations.

## Result
Model selection based on f1 score and AUC score give different results because their criteria for a good model are different.
Following is the F1 score of the classification models:
1. Logistic Regression: 0.8988
2. Decision Tree:       0.8614
3. Bagging:             0.8856
4. Random Forest:       0.8913
5. Boosting:            0.8905

Logistic regression model has the best performance, followed by Random Forest then Boosting and Bagging. Also, the time taken by Bagged tree and Boosting is the most but Logistic Regression is quite low comparatively yet providing a better f1 score. As expected, a single Decision Tree doesn't perform too well and gives lowest f1 score out of the five.
Following is the AUC score of the classification models:
1. Logistic Reg:    0.9668
2. Decision Tree:   0.8878
3. Bagging:         0.9656
4. Random Forest:   0.96404
5. Boosting:        0.9753

Model with largest Area Under Curve(AUC) is the best classification model.Boosting gives the best score out of all for the classification model. Although the scoring is very close, the order of best classification as per AUC score is Boosting followed by Logistic Regression then Bagging and then Random Forest. Decision Tree still has the lowest AUC (As seen in the graph as well).

## Conclusion
F1 does not take the true negatives into account and is a measure of precision and recall at a particular threshold value. High F1 implies both precision and recall are high.

F1-score： 2/(1/P+1/R) where  
Precision: TP/(TP+FP)  
Recall: TP/(TP+FN)

ROC/AUC： TPR=TP/(TP+FN), FPR=FP/(FP+TN)

For data like this as fraud detection, the positive examples(frauds) have relatively low rates of occurrence.
Due to this unbalance in data F1 score gets affected but not ROC/AUC. With imbalanced data, the AUC still gives value around 0.8. However, it is high due to large FP, rather than the large TP (True positive).
Therefore, F1 is a better evaluation metric in this case.
Roc/Auc is good with balanced distribution of positives and negatives in dataset.

