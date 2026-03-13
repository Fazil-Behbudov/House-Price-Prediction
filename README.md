# House Prices Regression Project (Kaggle - Ames Housing)

This repository contains my end-to-end workflow for the Kaggle competition
"House Prices: Advanced Regression Techniques".

The project starts from raw tabular data and goes through cleaning,
preprocessing, feature engineering, exploratory analysis, baseline modeling,
bonus experiments, and submission file generation.

## Problem Statement

Predict house sale prices (`SalePrice`) from structured home features for
properties in Ames, Iowa.

Competition page:
https://www.kaggle.com/c/house-prices-advanced-regression-techniques

## Project Highlights

- Full notebook workflow from data cleaning to model evaluation.
- Feature engineering with additional ratio, age, and interaction features.
- Baseline Linear Regression model with hold-out evaluation.
- Bonus experiments:
	- feature importance analysis
	- 5-fold cross-validation
	- polynomial features
	- feature scaling impact
- Kaggle-ready submission export (`Id`, `SalePrice`).

## Repository Structure

```text
House-Prices/
├── data/
│   ├── train/
│   └── test/
├── notebooks/
│   ├── 1-Data-Cleaning.ipynb
│   ├── 2-Data-Preprocessing.ipynb
│   ├── 3-Feature-Engineering.ipynb
│   ├── 4-Exploratory-Data-Analysis.ipynb
│   ├── 5-Linear-Regression-Homework.ipynb
│   └── submission.csv
├── data_description.txt
├── sample_submission.csv
├── requirements.txt
└── README.md
```

## Notebook Workflow

Run notebooks in this order:

1. `notebooks/1-Data-Cleaning.ipynb`
2. `notebooks/2-Data-Preprocessing.ipynb`
3. `notebooks/3-Feature-Engineering.ipynb`
4. `notebooks/4-Exploratory-Data-Analysis.ipynb`
5. `notebooks/5-Linear-Regression-Homework.ipynb`

The final notebook includes both required tasks and bonus tasks.

## Environment Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

Then launch Jupyter:

```bash
jupyter lab
```

## Modeling Results (Notebook 5)

Baseline Linear Regression metrics from the executed notebook:

- Train R2: `0.9292`
- Test R2: `0.8726`
- Test MSE: `0.01693`
- Test RMSE: `0.13012`
- Test MAE: `0.08741`
- Residual mean: `~0.00`

Bonus experiment summary:

- 5-fold CV mean R2: `0.4624` (std: `0.7768`) -> high fold variance.
- Polynomial (degree=2): Train R2 `1.0000`, Test R2 `0.6612`
	(clear overfitting).
- Linear Regression + StandardScaler: Test R2 `0.8726`
	(no material change vs unscaled baseline).

Note: The target in notebook 5 is modeled in transformed scale, so core
regression metrics are interpreted in that modeling space.

## Submission Output

The final notebook generates a Kaggle submission file in CSV format:

- Output columns: `Id`, `SalePrice`
- Output file: `notebooks/submission.csv`

## Key Takeaways

- A well-prepared baseline linear model can perform strongly on this dataset.
- Feature engineering contributes significantly to predictive quality.
- Polynomial expansion improved training fit but hurt test generalization.
- Scaling did not improve Linear Regression score, as expected.
- Cross-validation variance suggests sensitivity to data splits and motivates
	stronger validation strategy.

## Possible Next Improvements

- Use shuffled K-fold CV with fixed `random_state`.
- Add regularized linear models (Ridge, Lasso, ElasticNet).
- Compare with tree-based ensembles (Random Forest, XGBoost, LightGBM).
- Build a scikit-learn `Pipeline` for fully reproducible preprocessing.
- Add experiment tracking and a compact model comparison table.

## Coursework Context

This project was completed as a course assignment and keeps parts of the
original notebook task prompts for context.
