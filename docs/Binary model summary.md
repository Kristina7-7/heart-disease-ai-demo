## Binary Classification Summary

In this part of the project, I converted the original multiclass heart disease target into a binary classification problem:

- Class 0 = No heart disease
- Class 1 = Heart disease

The purpose of this change was to simplify the prediction task and focus on whether a patient has heart disease rather than predicting different levels of disease severity.

I trained and compared Logistic Regression, Decision Tree, and Random Forest models. I also used a DummyClassifier as a baseline model.

The DummyClassifier achieved approximately 54% accuracy because it predicted every patient as the majority class. However, it failed to identify any patients with heart disease, showing that accuracy alone is not enough to evaluate a medical classification model.

Among the trained models, Logistic Regression achieved the highest test accuracy of approximately 89%, followed by Random Forest at approximately 87% and Decision Tree at approximately 79%.

The ROC curve analysis also showed strong performance. Logistic Regression achieved the highest AUC of approximately 0.966, followed by Random Forest with 0.943 and Decision Tree with 0.860. This suggests that Logistic Regression had the strongest overall ability to distinguish between patients with and without heart disease in this experiment.

K-fold cross-validation was also used to evaluate model stability across different data splits. The cross-validation results showed some variation between folds, with an average score of approximately 0.855. This provides a more reliable estimate of model performance than relying on only one train-test split.

Overall, the binary classification analysis showed that the trained machine learning models performed substantially better than the baseline DummyClassifier. Logistic Regression showed the strongest overall performance based on both test-set accuracy and ROC-AUC. However, because this is a relatively small dataset, the results should be interpreted carefully and should not be considered sufficient for real clinical diagnosis.
