# Machine Learning Technologies - Assignment 1

**Student:** Hazem Daw  
**Group:** J4132  
**Course:** Machine Learning Technologies, ITMO University

## Overview

This project studies binary classification on the Bioresponse dataset. The goal is to predict the `Activity` of a molecule from its numerical descriptors and compare decision-tree and random-forest classifiers with different levels of complexity.

The work also includes a high-recall classifier designed to reduce Type II errors (false negatives), where an active molecule is incorrectly classified as inactive.

## Dataset

The dataset contains:

- 3,751 molecular samples
- 1,776 numerical descriptors (`D1` to `D1776`)
- A binary target column, `Activity`
- No missing values

The data is divided into a stratified 75% training set and 25% test set using `random_state=42`.

## Models

Four classifiers are trained and compared:

1. Small decision tree
2. Deep decision tree
3. Random forest with small trees
4. Random forest with deep trees

A fifth cost-sensitive random forest is trained with a larger weight for the positive class. Its decision threshold is selected on a validation subset of the training data to achieve high recall without using the test set for tuning.

## Evaluation

The models are evaluated using:

- Precision
- Recall
- Accuracy
- F1-score
- Log-loss
- Precision-recall curves
- ROC curves and ROC AUC

## Main Results

Among the four standard classifiers, the deep random forest produced the strongest overall result:

| Metric | Result |
| --- | ---: |
| Precision | 0.7790 |
| Recall | 0.8173 |
| Accuracy | 0.7751 |
| F1-score | 0.7977 |
| Log-loss | 0.4760 |
| ROC AUC | 0.8578 |

For the high-recall classifier, the selected decision threshold was `0.39`:

| Metric | Result |
| --- | ---: |
| Precision | 0.6370 |
| Recall | 0.9686 |
| Accuracy | 0.6834 |
| F1-score | 0.7685 |
| Log-loss | 0.5172 |

The high-recall model produced 16 false negatives on the test set and satisfies the assignment requirement of recall greater than 0.95.

## Repository Contents

- `Task_1_Hazem Daw_Group_J4132.ipynb` - completed notebook with code, results, and plots
- `bioresponse.csv` - dataset used in the assignment

## Running the Notebook

1. Download or clone this repository.
2. Keep the notebook and `bioresponse.csv` in the same directory.
3. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```

4. Open the notebook:

   ```bash
   jupyter notebook "Task_1_Hazem Daw_Group_J4132.ipynb"
   ```

5. Run all cells from top to bottom.

## Conclusion

The experiment shows how limiting tree depth affects model complexity and how combining many trees improves generalization. It also demonstrates the trade-off between precision and recall: lowering the classification threshold reduces false negatives, but increases the number of false positives.
