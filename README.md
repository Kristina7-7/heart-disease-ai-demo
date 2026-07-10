# Heart Disease Prediction using Machine Learning

## Project Overview

This project explores how machine learning can be used to predict heart disease using the UCI Heart Disease dataset.

The project is organized as a step-by-step learning portfolio, starting from data exploration and progressing to model interpretation.

---

## Dataset

- Dataset: UCI Heart Disease Dataset
- Number of patients: 303
- Features: 13 clinical variables
- Target: Heart disease severity (0–4)

---

## Project Structure

### Week 1 — Data Exploration

Completed:

- Load the dataset
- Understand clinical features
- Explore missing values
- Visualize feature distributions
- Correlation analysis

---

### Week 2 — Machine Learning Models

Completed:

- Train Logistic Regression
- Train Random Forest
- Evaluate both models
- Calculate Accuracy
- Generate Classification Reports
- Create Confusion Matrices

---

### Week 3 — Model Interpretation

Completed:

- Logistic Regression coefficient visualization
- Random Forest feature importance
- Confusion matrix visualization
- Model comparison
- Limitations

---

## Results

| Model | Accuracy |
|--------|----------|
| Logistic Regression | 54.1% |
| Random Forest | 50.8% |

Logistic Regression achieved slightly higher accuracy than Random Forest on this dataset.

---

## Figures
- Model comparison
  <img width="2670" height="1466" alt="model_performance_comparison" src="https://github.com/user-attachments/assets/9d992b55-7d2a-44b6-8645-cf1a20fa46ce" />

- Random forest feature important
  <img width="2370" height="1465" alt="feature_importance" src="https://github.com/user-attachments/assets/deb9f7a6-03f3-4e30-b0e8-7bb424e1b1e1" />

- Logistic regression confusion matrix
  <img width="1495" height="1361" alt="logistic_regression_confusion_matrix" src="https://github.com/user-attachments/assets/3653a514-709d-4543-af09-6539c15ea6f2" />

- Random forest confusion matrix
  <img width="1495" height="1361" alt="random_forest_confusion_matrix" src="https://github.com/user-attachments/assets/aa5a3a57-f0f2-42e8-a236-2fe98e4acb09" />

## Limitations

This project uses a small and imbalanced public dataset. Only two machine learning models were evaluated, and the results are based on one train-test split. The models have not been clinically validated and should not be used for medical diagnosis.

---

## Future Work

- Convert the target into binary classification
- Use cross-validation
- Perform hyperparameter tuning
- Test additional machine learning models
- Handle class imbalance
- Use larger cardiovascular datasets
- Explore ECG and CT angiography data
- Investigate medical imaging methods for blood clot detection

---

## Tools

- Python
- Google Colab
- Pandas
- Matplotlib
- Scikit-learn
- GitHub
