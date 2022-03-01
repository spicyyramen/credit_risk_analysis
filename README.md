# Credit Risk Analysis
The purpose of this analysis was to apply various sampling algorithms and classifiers to determine which was best suited for predicting credit risk.
<br>

# Results

## Naive Random Oversampling
The first sampling method utilized was the `RandomOverSampler` algorithm from `imblearn.over_sampling` in conjunction with the `LogisticRegression` model.<br>

### *Balanced Accuracy Score*
The accuracy score of using `RandomOverSampler` with `LogisticRegression` was fairly low at only 65.8%.<br>

![Balanced Accuracy Score- ROS](./images/ros_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, you can see that the model rarely misclassifies high risk applicants as low risk. Alternatively, the model very frequently misclassifies low risk applicants as high risk.<br>

The confusion matrix demonstrates why this model and sampling method is inadequate for predicting credit risk- while it may do well at preventing high risk applications from making it through, it also misclassifies the majority of low risk applications as high risk- which would lead to many qualified applications being denied.<br>

![Confusion Matrix- ROS](./images/ros_CM.png)<br>

![Confusion Matrix (dataframe format)- ROS](./images/ros_CM-df.png)<br>

### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.01, the precision was very low
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.70, the precision was moderate
- **low risk**: at 0.61, the precision was low
<br>  

![Imbalanced Classification Report- ROS](./images/ros_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `RandomOverSampler` with `LogisticRegression` indicate that this model *is not* suitable for predicting credit risk.

<br>
<br>


## Oversampling - SMOTE
The next sampling method utilized was the `SMOTE` algorithm from `imblearn.over_sampling` in conjunction with the `LogisticRegression` model.<br>

### *Balanced Accuracy Score*
The accuracy score of using `SMOTE` with `LogisticRegression` was similar to naive oversampling at just 66.2%.<br>

![Balanced Accuracy Score- SMOTE](./images/smote_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, this sampling method decreased the amount of low risk applications that are misclassified as high risk. However, there were still over 5000 applications misclassified as high risk, which would again prevent qualified applicants from being approved.
<br>

![Confusion Matrix- SMOTE](./images/smote_CM.png)<br>


### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.01, the precision was very low
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.63, the precision was low
- **low risk**: at 0.69, the precision was low
<br> 

![Imbalanced Classification Report- ROS](./images/smote_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `SMOTE` with `LogisticRegression` indicate that this model, while slightly better than the previous, *is not* suitable for predicting credit risk.


<br>
<br>



## Undersampling - Cluster Centroids
The next sampling method utilized was the `ClusterCentroids` algorithm from `imblearn.under_sampling` in conjunction with the `LogisticRegression` model.<br>

### *Balanced Accuracy Score*
The accuracy score of using `ClusterCentroids` with `LogisticRegression` was lower than both oversampling methods, at just 54.5%- which is hardly better than random chance.<br>

![Balanced Accuracy Score- Cluster Centroids](./images/cluster_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, this sampling method resulted in over 10,000 low risk applications being classified as high risk. It seems the model is highly biased toward classifying applications as high risk. 
<br>

![Confusion Matrix- Cluster Centroids](./images/cluster_CM.png)<br>


### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.01, the precision was very low
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.69, the precision was low
- **low risk**: at 0.40, the precision was very low
<br> 

![Imbalanced Classification Report- Cluster Centroids](./images/cluster_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `ClusterCentroids` undersampling with `LogisticRegression` indicate that this model performed even worse than our previous oversampling methods, and *is not* suitable for predicting credit risk.


<br>
<br>



## Combination Sampling - SMOTEENN
The next sampling method utilized was the `SMOTEENN` algorithm from `imblearn.combine` in conjunction with the `LogisticRegression` model.<br>

### *Balanced Accuracy Score*
The accuracy score of using `SMOTEENN` with `LogisticRegression` was better than all previous methods at 69.5%. While this is an improvement from the other models, it is still a fairly low score.<br>

![Balanced Accuracy Score- SMOTEENN](./images/smoteenn_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, this sampling method once again resulted in a large number of low risk applications being misclassified as high risk. Although, this model had the lowest number of high risk applications misclassified as low risk. This indicates the model is slightly more effective at preventing high risk applications from 'slipping through the cracks'. 
<br>

![Confusion Matrix- SMOTEENN](./images/smoteenn_CM.png)<br>


### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.01, the precision was very low
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.79, the precision was moderate
- **low risk**: at 0.60, the precision was low
<br> 

![Imbalanced Classification Report- SMOTEENN](./images/smoteenn_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `SMOTEENN` sampling with `LogisticRegression` indicate that this model performed slightly better than all previous models, but is still not very effective at predicting credit risk.


<br>
<br>



## Ensemble - Balanced Random Forest Classifier
The next sampling method utilized was the `BalancedRandomForestClassifier` algorithm from `imblearn.ensemble`.<br>

### *Balanced Accuracy Score*
The accuracy score of using `BalancedRandomForestClassifier` was higher than all previous models at 76.1%. This score is significantly better than the previous models.<br>

![Balanced Accuracy Score- Balanced Random Forest Classifier](./images/brfc_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, this sampling method once again resulted in a large number of low risk applications being misclassified as high risk. Although, this model had the lowest number of high risk applications misclassified as low risk. This indicates the model is slightly more effective at preventing high risk applications from 'slipping through the cracks'. 
<br>

![Confusion Matrix- Balanced Random Forest Classifier](./images/brfc_CM.png)<br>


### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.03, the precision was low
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.64, the precision was fairly low
- **low risk**: at 0.88, the precision is acceptable
<br> 

![Imbalanced Classification Report- Balanced Random Forest Classifier](./images/brfc_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `BalancedRandomForestClassifier` indicate that this model performed slightly better than all previous models, and is approaching a model with sufficient predictive power.


<br>
<br>



## Ensemble - Easy Ensemble Classifier
The next sampling method utilized was the `EasyEnsembleClassifier` algorithm from `imblearn.ensemble`.<br>

### *Balanced Accuracy Score*
The accuracy score of using `EasyEnsembleClassifier` was the highest performing model at 93.2%.<br>

![Balanced Accuracy Score- Easy Ensemble Classifierr](./images/eec_balanced-acc.png)<br>

### *Confusion Matrix*
Looking at the confusion matrix, this sampling method once again resulted in a large number of low risk applications being misclassified as high risk. Although, this model had the lowest number of high risk applications misclassified as low risk. This indicates the model is slightly more effective at preventing high risk applications from 'slipping through the cracks'. 
<br>

![Confusion Matrix- Easy Ensemble Classifier](./images/eec_CM.png)<br>


### *Imbalanced Classification Report*
Precision:
- **high risk**: at 0.09, the precision was low, but 9x better than all other models
- **low risk**: at 1.0, the precision is high<br>

Recall:
- **high risk**: at 0.92, the precision was high
- **low risk**: at 0.94, the precision was high
<br> 

![Imbalanced Classification Report- Easy Ensemble Classifier](./images/eec_imbalanced-class.png)<br>

### *Review*
Overall, the various metrics utilized to evaluate the use of `EasyEnsembleClassifier` indicate that this model was the most effective at accurately predicting credit risk. 


# Summary & Suggestion
Based on all the models and sampling methods tested, use of the `EasyEnsembleClassifier` from `imblearn.ensemble` was by far the most effective at predicting credit risk. With an accuracy score of 93% and recall values in the 90+% range, this model is an acceptable model for this application.