# SELF AUDIT

## Project
UCI Heart Disease AI Demo

### Purpose

This self-audit was completed after reviewing my project using the instructor's evaluation checklist. The goal was to identify conceptual mistakes, improve the implementation, and make the project more reproducible and scientifically accurate.

---

## Corrections

| Original                                                                            | Problem                                                                                                                                           | Correction                                                                                                                                            | Verification                                                                                                 |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Interpreted `model.coef_[0]` as the overall effect on heart disease.                | In a multiclass Logistic Regression model, each row of `coef_` corresponds to one class rather than the overall disease prediction.               | Updated the explanation to describe each coefficient as the relationship between a transformed feature and one specific class.                        | Verified using `pipeline.named_steps["model"].classes_` and `pipeline.named_steps["model"].coef_.shape`.     |              
| Filled missing values before splitting the dataset.                                 | Filling missing values before the train-test split may introduce data leakage because information from the test set is used during preprocessing. | Replaced manual imputation with `SimpleImputer` inside separate numeric and categorical pipelines within a `ColumnTransformer`.                       | Verified that preprocessing is performed only during `pipeline.fit(X_train, y_train.values.ravel())`.        |
| Used a train-test split without stratification.                                     | Random splitting may produce an uneven class distribution between the training and testing sets.                                                  | Added `stratify=y` in `train_test_split()` to preserve the class proportions in both sets.                                                            | Compared the class distributions before and after using stratified sampling.                                 |
| Treated categorical variables as numerical values.                                  | Logistic Regression may incorrectly assume an ordinal relationship between category labels.                                                       | Processed categorical features with `OneHotEncoder` and continuous features with `StandardScaler` using a `ColumnTransformer`.                        | Verified the transformed feature names using `pipeline.named_steps["preprocessor"].get_feature_names_out()`. |
| Trained the Logistic Regression model without an integrated preprocessing workflow. | Separate preprocessing steps are harder to reproduce and increase the risk of inconsistent data handling.                                         | Built a complete `Pipeline` that combines preprocessing and model training into a single workflow.                                                    | Verified by successfully training and predicting using `pipeline.fit()` and `pipeline.predict()`.            |


## Reflection

This self-audit helped me improve both the implementation and documentation of the project. I corrected potential data leakage, applied appropriate preprocessing for different feature types, used stratified sampling, and built a reproducible machine learning pipeline. This process made the project more reliable and better aligned with standard machine learning practices.
