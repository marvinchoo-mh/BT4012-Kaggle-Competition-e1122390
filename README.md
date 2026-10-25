# BT4012 Kaggle Competition 2026: detecting illicit Bitcoin transactions

**Student:** Marvin Choo Ming Han (E1122390)

The task is to rank Bitcoin transactions by how likely they are to be illicit. The data has 157,101 transactions
with 165 anonymised features each, plus the payment links between them. Training covers time steps 1–35 and the
test set covers steps 36–49. Submissions are scored by ROC-AUC.

This repository reproduces the two submissions I selected for the final leaderboard:

| Notebook | Model | Output file | Public ROC-AUC | Run time |
|---|---|---|---|---|
| `e1122390.ipynb` | Ensemble of 11 graph-stacked models (main submission) | `Submission/e1122390.csv` | 0.96974 | 30–45 min |
| `submission_2_e1122390.ipynb` | Single XGBoost on 44 selected features | `Submission/submission_2_e1122390.csv` | 0.95441 | about 1 min |

Both notebooks are saved with their outputs, so you can read the results without running them. The report is
`e1122390.pdf`.

## 1. Get the data

The dataset is not included in this repository. Download the four files from the BT4012 Kaggle competition page:


Put them in the `data/` folder:

```
data/
├── train.csv
├── test.csv
├── txs_edgelist.csv
└── sample_submission.csv
```

Both notebooks read the data from `data/`, relative to the repository root.

## 2. Install

Python 3.11. On macOS, LightGBM and XGBoost also need OpenMP (`brew install libomp`).

```
pip install -r requirements.txt
```

## 3. Reproduce the submissions

Run each notebook from the repository root, either in Jupyter or from the command line:

```
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 e1122390.ipynb
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 submission_2_e1122390.ipynb
```

Each notebook writes its submission file to `Submission/`. The files already in `Submission/` are the ones I
submitted, so you can compare a fresh run against them.


## Repository layout

```
e1122390.ipynb                 final model (main submission)
submission_2_e1122390.ipynb    second submission
e1122390.pdf                   report
requirements.txt               Python packages and versions
data/                          put the competition files here (not included)
Submission/                    submission files written by the notebooks
report/figures/                figures saved by e1122390.ipynb
```
