# UCI Heart Disease Machine Learning Demo

## Project Overview

This project explores how machine learning can be applied to clinical tabular data for heart disease prediction using the UCI Heart Disease dataset.

The project started with multiclass classification using the original disease labels from 0 to 4. It was later extended to binary classification to predict whether heart disease is present or absent.

The main goals of this project are to practice data preprocessing, machine learning model training, model evaluation, and interpretation in a healthcare-related dataset.

---

## Dataset

The project uses the UCI Heart Disease dataset.

The dataset contains clinical information related to heart disease, including 13 commonly used features:

- `age` — Age
- `sex` — Sex
- `cp` — Chest pain type
- `trestbps` — Resting blood pressure
- `chol` — Serum cholesterol
- `fbs` — Fasting blood sugar
- `restecg` — Resting electrocardiographic results
- `thalach` — Maximum heart rate achieved
- `exang` — Exercise-induced angina
- `oldpeak` — ST depression induced by exercise relative to rest
- `slope` — Slope of the peak exercise ST segment
- `ca` — Number of major vessels
- `thal` — Thalassemia-related test result

The original target variable contains five classes:

- 0 = No heart disease
- 1–4 = Different levels/categories of heart disease

---

## Part 1: Multiclass Classification

The first part of the project used the original target labels from 0 to 4.

The models explored included:

- DummyClassifier
- Logistic Regression
- Decision Tree
- Random Forest

The multiclass task was more difficult because the model needed to distinguish among five different classes, including several classes with relatively small sample sizes.

Evaluation included:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- Classification report

This part of the project helped demonstrate why accuracy alone is not enough to evaluate a medical classification model, especially when the classes are imbalanced.

---

## Part 2: Binary Classification

The original target was converted into a binary classification problem:

- 0 = No heart disease
- 1 = Heart disease present

Original classes 1–4 were combined into the disease-positive class.

This simplified the prediction task and allowed the models to focus on whether heart disease was present rather than predicting the original disease category.

---

## Data Preprocessing

Different preprocessing methods were applied to numerical and categorical features.

### Numerical Features

Numerical features were processed using:

- `SimpleImputer(strategy="median")` for missing values
- `StandardScaler()` for standardization

### Categorical Features

Categorical features were processed using:

- `SimpleImputer(strategy="most_frequent")` for missing values
- `OneHotEncoder(handle_unknown="ignore")` for categorical encoding

A `ColumnTransformer` was used to apply the appropriate preprocessing method to each feature type.

The preprocessing steps and machine learning models were combined using Scikit-learn `Pipeline` objects.

This helps prevent data leakage and ensures that the same preprocessing workflow is applied consistently during training and prediction.

---

## Train-Test Split

The dataset was divided into training and testing sets using an 80/20 split.

Stratified sampling was used:

`stratify=y`

This helps preserve approximately the same proportion of each target class in the training and testing datasets.

`random_state=42` was used to make the split reproducible.

---

## Models

Four models were compared:

### DummyClassifier

The DummyClassifier was used as a baseline.

It predicts the most frequent class without learning meaningful relationships from the clinical features.

### Logistic Regression

Logistic Regression provides a relatively simple and interpretable classification approach.

### Decision Tree

The Decision Tree makes predictions using a series of feature-based decision rules.

Tree depth was limited to reduce the risk of overfitting.

### Random Forest

Random Forest combines predictions from multiple decision trees.

In this project, 100 trees were used.

---

## Binary Classification Results

On the test set, the approximate model accuracies were:

| Model | Test Accuracy |
|---|---:|
| DummyClassifier | 54.1% |
| Decision Tree | 78.7% |
| Random Forest | 86.9% |
| Logistic Regression | 88.5% |

Logistic Regression achieved the highest test accuracy.

Both Logistic Regression and Random Forest also achieved a recall of approximately 0.93 for the heart-disease class, meaning they detected most of the disease-positive patients in this test set.

Because this is a small dataset, these results should not be interpreted as clinical performance.

---

## ROC Curve Analysis

ROC curves were used to evaluate how well the trained models distinguished between patients with and without heart disease across different classification thresholds.

The observed ROC-AUC values were approximately:

| Model | ROC-AUC |
|---|---:|
| Logistic Regression | 0.966 |
| Random Forest | 0.943 |
| Decision Tree | 0.860 |

Logistic Regression achieved the highest ROC-AUC in this experiment.

The DummyClassifier was used as a baseline but was not included in the main ROC comparison.

---

## Stratified K-Fold Cross-Validation

To evaluate whether model performance was dependent on a single train-test split, 5-fold Stratified Cross-Validation was performed for Logistic Regression.

The five accuracy scores were approximately:

- 0.934
- 0.820
- 0.836
- 0.800
- 0.883

Mean cross-validation accuracy:

**0.855 (85.5%)**

The cross-validation result was reasonably close to the single test-set accuracy, suggesting that the model showed relatively consistent performance across different subsets of the dataset.

---

## Key Learning Points

Through this project, I learned how to:

- Work with a real healthcare-related tabular dataset
- Distinguish numerical and categorical features
- Handle missing values using imputation
- Use OneHotEncoder for categorical variables
- Standardize numerical features
- Build reproducible Scikit-learn pipelines
- Use stratified train-test splitting
- Compare multiple machine learning models
- Use a DummyClassifier as a baseline
- Interpret confusion matrices
- Compare accuracy, precision, recall, and F1-score
- Use ROC curves and ROC-AUC
- Use Stratified K-Fold Cross-Validation
- Understand the difference between multiclass and binary classification

---

## Limitations

This project is an educational machine learning demonstration and is not intended for clinical diagnosis.

Important limitations include:

- The dataset is relatively small.
- The data may not represent modern or diverse patient populations.
- Model performance may vary across different train-test splits.
- Combining disease classes 1–4 into one binary class removes information about the original disease categories.
- High model performance on this dataset does not mean the model is ready for clinical use.
- External validation on independent patient populations would be necessary before considering real clinical applications.

---

## Conclusion

This project demonstrates a complete introductory machine learning workflow using heart disease data.

The binary classification task produced stronger classification performance than the original multiclass task. Among the models tested, Logistic Regression showed the strongest overall results in this experiment, including high test accuracy and ROC-AUC.

More importantly, the project demonstrates that medical AI evaluation should not rely only on accuracy. Metrics such as recall, precision, F1-score, ROC-AUC, baseline comparison, and cross-validation provide a more complete understanding of model performance.
