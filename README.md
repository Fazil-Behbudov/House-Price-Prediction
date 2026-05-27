# House Prices Regression (Kaggle - Ames Housing)

Portfolio-ready end-to-end workflow for the Kaggle competition
"House Prices: Advanced Regression Techniques".

Competition page:
https://www.kaggle.com/c/house-prices-advanced-regression-techniques

## Highlights

- Full pipeline: cleaning, preprocessing, feature engineering, EDA, modeling.
- Baseline Linear Regression plus regularized and tree-based models.
- Cross-validation and model blending for stronger generalization.
- Kaggle submission generation with reproducible preprocessing.
- Public leaderboard RMSE: **0.16475**.

## Repository Structure

```text
House-Price-Prediction/
├── data/                 # ignored in git (raw + processed datasets)
├── data_info/            # ignored in git (data description, references)
├── notebooks/
│   ├── 1-Data-Cleaning.ipynb
│   ├── 2-Data-Preprocessing.ipynb
│   ├── 3-Feature-Engineering.ipynb
│   ├── 4-Exploratory-Data-Analysis.ipynb
│   ├── 5-Linear-Regression-Homework.ipynb
│   └── 6-Advanced-Modeling.ipynb
├── submissions/          # ignored in git (generated CSVs)
├── requirements.txt
└── README.md
```

## Data (Not Committed)

The raw Kaggle dataset and generated artifacts are ignored in git.

1. Download the competition data from Kaggle.
2. Place files in the expected structure:

```text
data/
  train/train.csv
  test/test.csv
```

If you want the data description file locally, place it in `data_info/`.

## Notebook Workflow

Run notebooks in order:

1. **1-Data-Cleaning.ipynb** — Handle missing values, outliers, and data quality issues.
2. **2-Data-Preprocessing.ipynb** — Feature scaling, categorical encoding, and train/test split.
3. **3-Feature-Engineering.ipynb** — Create new features, polynomial terms, and feature interactions.
4. **4-Exploratory-Data-Analysis.ipynb** — Correlations, distributions, and key insights.
5. **5-Linear-Regression-Homework.ipynb** — Baseline models: Linear Regression, Ridge, Lasso, ElasticNet.
6. **6-Advanced-Modeling.ipynb** — Tree-based models (XGBoost, LightGBM, Random Forest), hyperparameter tuning, ensemble blending.

Notebook 6 exports the Kaggle submission CSV to `submissions/` (ignored in git).

## Environment Setup

Windows:

```bash
python -m venv venv
venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

macOS/Linux:

```bash
python -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

Then launch Jupyter:

```bash
jupyter lab
```


### Model Performance (Test Set)

| Model | RMSE | R² Score |
|-------|------|----------|
| XGBoost | 0.0896 | 0.9230 |
| LightGBM | 0.0968 | 0.9100 |
| Lasso | 0.0986 | 0.9066 |
| ElasticNet | 0.1033 | 0.8975 |
| Random Forest | 0.1043 | 0.8955 |
| Ridge | 0.1107 | 0.8824 |
| Linear Regression | 0.1189 | 0.8643 |

### Ensemble Strategy

- **Best Individual Model**: XGBoost (RMSE: 0.0896)
- **Best Ensemble**: Tuned blend of XGBoost + LightGBM + ElasticNet + Lasso
  - **Final Test RMSE**: 0.0881 | **R²**: 0.9254
- **CV Stability**: ElasticNet achieved best cross-validation RMSE (0.1180) with strong regularization

Detailed metrics, CV results, and model blending strategy documented in `notebooks/5-Linear-Regression-Homework.ipynb` and `notebooks/6-Advanced-Modeling.ipynb`.

## Notes

This project started as coursework and has been cleaned and structured for a
portfolio-style presentation.
