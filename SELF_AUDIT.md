# SELF AUDIT

## Project
UCI Heart Disease AI Demo

### Purpose

This self-audit was completed after reviewing my project using the instructor's evaluation checklist. The goal was to identify conceptual mistakes, improve the implementation, and make the project more reproducible and scientifically accurate.

---

## Corrections

| Original | Problem | Correction | Verification |
|----------|---------|------------|--------------|
| Interpreted `model.coef_[0]` as the overall effect on heart disease. | In a multiclass Logistic Regression model, each row of `model.coef_` corresponds to one class rather than the entire disease prediction. | Updated the explanation to describe each coefficient as the relationship between a feature and one specific class. | Verified using `model.classes_` and `model.coef_.shape`. |
| Did not compare the model with a simple baseline. | Without a baseline, it is difficult to know whether the model actually learned useful information. | Added a `DummyClassifier` that always predicts the majority class and compared its performance with Logistic Regression and Random Forest. | Compared the number of correctly predicted patients for each model. |
| Filled missing values before splitting the dataset. | This introduces slight data leakage because statistics were calculated using the entire dataset. | Replaced manual imputation with `SimpleImputer` inside a Pipeline so preprocessing is learned only from the training set. | Reviewed the preprocessing workflow before and after modification. |
| Used a single train-test split without stratification. | Minority classes may be unevenly distributed between training and testing sets. | Added `stratify=y` and planned to use `StratifiedKFold` for future experiments. | Compared the class distributions before and after stratified sampling. |
| Treated several categorical variables as numerical values. | Logistic Regression may incorrectly assume numerical ordering between categories. | Planned to preprocess categorical variables using `OneHotEncoder` and continuous variables using `StandardScaler`. | Reviewed feature types and preprocessing strategy. |

---

## Reflection

This self-audit helped me understand that building a machine learning model is not only about obtaining higher accuracy. Correct preprocessing, appropriate evaluation metrics, careful interpretation of model outputs, and comparison with simple baseline models are all essential for producing reliable medical AI results. If I continue this project, I will rebuild the entire pipeline using `Pipeline`, `ColumnTransformer`, `OneHotEncoder`, and cross-validation to improve both reproducibility and model performance.
