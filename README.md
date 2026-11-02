# Vehicle Insurance Portfolio & Risk Analysis

An exploratory data analysis project for vehicle insurance records. The analysis is in [`eda-project.ipynb`](eda-project.ipynb) and uses the CSV files in `archive/`.

## Project contents

- `eda-project.ipynb` — loads and combines the source CSVs, reviews data quality, summarizes fields, and explores vehicle types, makes, policy dates, premiums, insured values, and engine capacity.
- `archive/motor_data11-14lats.csv` and `archive/motor_data14-2018.csv` — source insurance records.
- `requirements.txt` — Python packages used by the notebook.

## Run the analysis

Use Python 3.12 or a compatible Python 3 environment. From the project directory, install the dependencies and open the notebook in Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook eda-project.ipynb
```

The requirements install the notebook's Python kernel and analysis libraries. Install Jupyter Notebook or JupyterLab separately if it is not already available in your environment.

The notebook searches `archive/` and `datasets/` (if present) for files matching `motor_data*.csv`. To use another folder or filename pattern, edit `DATA_DIRS` or `FILE_PATTERN` in the first code cell.

## Data handling notes

- Each source row is treated as an insurance record. Repeated `OBJECT_ID` values may refer to the same vehicle across policy years; row counts are not unique vehicle counts unless records are deduplicated.
- The source filename is retained in a `SOURCE_FILE` column when files are combined.
- Numeric fields and policy dates are parsed where possible. Invalid or blank values stay missing; the notebook does not fill them with assumed values.
- Fields such as `SEX`, `INSR_TYPE`, and `EFFECTIVE_YR` are coded. Use a reliable data dictionary before interpreting their codes.
- The provided CSVs do not include policyholder age, marital status, anti-theft devices, or coverage details.
