# Week 1 Summary

## Goal

Learn the basic workflow of a biomedical AI project using the UCI Heart Disease dataset.

---

## What I completed

- Created a GitHub repository.
- Learned how to use Google Colab.
- Loaded the UCI Heart Disease dataset.
- Explored the dataset using `X.head()-first five rows`, `X.info()-total count+ missing value`, and `X.describe()`-find max/min/std.
- Learned the meaning of all 13 clinical features.
- Checked missing values.
- Created basic data visualizations, using 'import matplotlib.pyplot as plt'
- Saved the figures, using 'plt.savefig("title.png", dpi=300, bbox_inches="tight")'


---

## Key findings

- The dataset contains 303 patients.
- There are 13 input features.
- The `ca` and `thal` columns contain missing values.
- The target classes are imbalanced.

---

## What I learned

- A machine learning model uses patient features (X) to predict heart disease (y).
- Understanding the dataset is important before building a model.
- GitHub is used to organize and share project files.

---

## Questions

- Why do `ca` and `thal` have missing values?
- Why do many tutorials convert the target into binary classification?
