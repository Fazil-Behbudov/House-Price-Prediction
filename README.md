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

1. `notebooks/1-Data-Cleaning.ipynb`
2. `notebooks/2-Data-Preprocessing.ipynb`
3. `notebooks/3-Feature-Engineering.ipynb`
4. `notebooks/4-Exploratory-Data-Analysis.ipynb`
5. `notebooks/5-Linear-Regression-Homework.ipynb`
6. `notebooks/6-Advanced-Modeling.ipynb`

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

## Results

Model metrics, plots, and CV results are documented in notebooks 5 and 6.
The advanced notebook includes an ensemble blend and a Kaggle-ready submission.

## Notes

This project started as coursework and has been cleaned and structured for a
portfolio-style presentation.
