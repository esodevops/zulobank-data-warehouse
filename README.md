# ZuloBank Data Engineering Project

This project uses a Jupyter notebook workflow to transform the raw `zulo_bank.csv` dataset into a normalized relational model and warehouse-style outputs for banking analytics.

## Overview

The main notebook, `zulobank_notebook.ipynb`, performs these steps:

1. Loads the raw banking dataset from `dataset/zulo_bank.csv`.
2. Cleans missing loan-related fields.
3. Splits customer names into first and last names.
4. Normalizes the source data into customer, account, transaction, and loan tables.
5. Builds a date dimension for downstream modeling.
6. Produces database-model and data-warehouse output files stored under `dataset/`.

## Project Structure

```text
ZuloBank/
├── zulobank_notebook.ipynb
├── dataset/
│   ├── zulo_bank.csv
│   ├── database_model/
│   ├── loan_dwh/
│   └── transaction_dwh/
├── images/
│   ├── db_schema.png
│   ├── loans_dwh_schema.png
│   ├── transactions_dwh_schema.png
│   └── zulo_bank.drawio
└── zulobank_ENV/
```

## Data Outputs

The repository already contains generated CSV outputs in these folders:

- `dataset/database_model/`: normalized entity and fact-style tables such as customers, accounts, loans, transactions, and date dimensions.
- `dataset/loan_dwh/`: loan warehouse dimensions and fact table.
- `dataset/transaction_dwh/`: transaction warehouse dimensions and fact table.

## Requirements

Install dependencies from `requirements.txt`:

```bash
pip install -r requirements.txt
```

The notebook uses Python with:

- `pandas`
- `jupyter`
- standard library `datetime`

The workspace already includes a local virtual environment in `zulobank_ENV/`.

## Running The Notebook

### Option 1: Use the existing local environment

```bash
source zulobank_ENV/bin/activate
jupyter notebook
```

Then open `zulobank_notebook.ipynb` and run the cells in order.

### Option 2: Recreate the environment manually

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

## Modeling Notes

- The notebook demonstrates normalization from a denormalized source into 1NF, 2NF, and 3NF style structures.
- A date dimension is generated programmatically for warehouse use.
- The diagrams in `images/` document the source schema and warehouse schema designs.

## Main Files

- `zulobank_notebook.ipynb`: transformation logic and exploratory workflow.
- `requirements.txt`: notebook dependencies.
- `dataset/zulo_bank.csv`: source dataset.
- `images/zulo_bank.drawio`: editable schema diagram.
- `images/db_schema.png`: database-model schema image.
- `images/transactions_dwh_schema.png`: transaction warehouse schema image.
- `images/loans_dwh_schema.png`: loan warehouse schema image.

## Notes

- The `.gitignore` excludes the local virtual environment and notebook/cache artifacts so local tooling does not pollute version control.
- If you regenerate outputs, review the CSV files in `dataset/` before committing changes.
