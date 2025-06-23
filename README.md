# Data-Analysis

Hands-on data analysis practice using Pandas, EDA, and SQL

### Command to create a conda environment:

conda create -p venv python==3.10

### To install Pandas and NumPy inside your Conda environment, just activate the environment and run:

conda activate venv

<!-- conda activate ./venv -->

conda install pandas numpy

### Python package to run an IPython notebook file in VS Code:

`pip install ipykernel` # For running Jupyter notebooks in VS Code

This package is a kernel that is responsible for executing Python code in an IPython notebook.

## Export the Environment

Run this command to create a file with all packages and versions:
`conda env export > environment.yml`

### Use --from-history to Auto-Create a Clean Version

This only includes what you explicitly installed (not all dependencies):
`conda env export --from-history > environment.yml`

## Data Analysis Practice

This repository contains my step-by-step practice and notes for preparing for data analysis interviews. It includes:

- Pandas fundamentals
- Data cleaning & transformation
- EDA & visualizations
- SQL queries and case studies
- Real dataset notebooks

## Structure

- `datasets/` – Raw CSV files
- `notebooks/` – Jupyter notebooks
- `notes/` – Interview prep notes and cheatsheets
- `outputs/` – Final output file

| File Name                       | Purpose                                       |
| ------------------------------- | --------------------------------------------- |
| `pandas_essentials.md`          | Basics: loading, cleaning, renaming, nulls    |
| `pandas_groupby_filtering.md`   | Filtering, sorting, groupby, aggregation      |
| `pandas_eda_visualization.md`   | EDA, plotting, correlation heatmaps           |
| `pandas_interview_questions.md` | Pandas-focused Q\&A with real interview-style |
| `sql_basics.md`                 | SQL SELECT, JOIN, WHERE, GROUP BY             |
| `sql_interview_questions.md`    | SQL interview questions & window functions    |
