# Divvy-Bikes
I will be living in the Chicago area soon as part of my Master's program at the University of Chicago. As someone who enjoyed using the electric bikes and scooters located on my undergrad campus, UCLA, I wanted to analyze some behaviors and patterns from the Chicago bike-sharing system that also services the UChicago campus area, Divvy.

Divvy provides its past ride data [here](https://divvy-tripdata.s3.amazonaws.com/index.html). Learn more about Divvy's data collection and terms [here](https://divvybikes.com/system-data) I am using the ride data from the past year, so from May 2022 to May 2023, both in my quick cursory study as well as in my model building.

**Disclaimer**: I do not own any of the data used. All rights are with Divvy and Motivate.

After cleaning and processing, the total size of the data came out to be around ~6.3 million rows, which I split into training, validation, and testing via a 98, 1, 1 split.

This allowed me to be at 99% confidence with a margin of error close to 0.5% that the models' performances on the test set was consistent.

I built and finalized 9 different classifier models to predict member vs non-member status. These were:
- a Logistic Regression classifier, which served as my baseline.
- a Naive Bayes model
- a (baseline) Decision Tree Classifier
- a (hyperparameter-tuned) Decision Tree Classifier
- a (hyperparameter-tuned) Random Forest Classifier
- a (hyperparameter-tuned) XGBoost Classifier
- a (baseline) LightGBM Classifier
- a (partially-tuned) LightGBM Classifier
- a (hyperparameter-tuned) LightGBM Classifier.

Ultimately, the hyperparameter-tuned LightGBM Classifier was the best-performing model, achieving an AUC of above 0.80 on both the validation and testing datasets.

## Contents:
**study.ipynb**: This is the notebook I used to perform a quick, preliminary, no-modeling study on the dataset(s) and the basic trends between members and non-members.

**classification.ipynb**: This is the notebook I used to build, validate, tune, and test all the classifier models I built.

## Files
### figs
This is the collection of figures and plots from the classifiers. Files included:
- **ROC_curves**: image of all the ROC curves for the 9 classifier models.
- **base_lgb_conf**: confusion matrix for the baseline LightGBM Classifier.
- **base_lgb_f_score_importances**: feature importances for the baseline LightGBM Classifier by f-score rather than gini.
- **base_tree_conf**: confusion matrix for the baseline Decision Tree Classifier.
- **base_tree_importances**: feature importances for the baseline Decision Tree Classifier.
- **base_tree_plot**: plot of the first levels/splits of the baseline Decision Tree Classifier.
- **day_of_week_hist**: histogram of rides based on what day of week they occur, separated by member status.
- **heatmap**: heatmap of the features in the processed dataset.
- **log_reg_conf**: confusion matrix for the baseline Logistic Regression model.
- **nb_conf**: confusion matrix for the Naive Bayes model.
- **opt_lgb_conf**: confusion matrix for the hyperparameter-tuned LightGBM Classifier.
- **opt_lgb_f_score_importances**: feature importances for the hyperparameter-tuned LightGBM Classifier by f-score rather than gini.
- **opt_tree_conf**: confusion matrix for the hyperparameter-tuned Decision Tree Classifier.
- **opt_tree_importances**: feature importances for the hyperparameter-tuned Decision Tree Classifier.
- **opt_tree_plot**: plot of the first levels/splits of the hyperparameter-tunned Decision Tree Classifier.
- **random_forest_conf**: confusion matrix for the Random Forest Classifier.
- **random_forest_importances**: feature importances for the Random Forest Classifier.
- **time_of_day**: histogram of rides based on what time of day they occur, separated by member status.
- **tuned_lgb_conf**: confusion matrix for the partially-tuned LightGBM Classifier.
- **tuned_lgb_f_score_importances**: feature importances for the partially tuned LightGBM Classifier by f-score rather than gini.
- **xgb_conf**: confusion matrix for the XGBoost Classifier.
- **xgb_f_score_importances**: feature importances for the XGBoost Classifier by f-score rather than gini.
- **xgb_importances**: feature importances for the XGBoost Classifier.

### results
These are the results of the models by AUC, Accuracy, Precision, Recall, and f-1.
- **results.pkl**: validation results,
- **test_results.pkl**: final testing set results.
