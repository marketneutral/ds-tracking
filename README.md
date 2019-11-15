# Notes on Data Science Experiment Tracking, Collaboration, and Reproducibility

What is the optimal way for a small team to collaborate on a Kaggle competition?

## Existing Solutions

- Neptune
- bias and weights
- mlflow
- dvc
- sacred

## Open questions

- What solution works best with *minimal to no* change of workflow? The key being that most data science work is done in Jupyter notebooks. 
- Can we use `papermill` parameterization and execution along with git only?

## Sketch idea

- `papermill` parameterization
- `papermill` `pm.record(...)` in each notebook the metrics; output every run to `/output/<hash>.ipynb`
- In a dashboard nb, `nbs = pm.read_notebooks('output/')` where `nbs.dataframe` contains all items recorded in *all* notebooks/experiments
- Never touch anything in the output directory
- Every experiment is run as a papermill nb; a hash per notebook which is embedded in any filename (output nb; submission file, etc.) and this hash is noted in git commit

