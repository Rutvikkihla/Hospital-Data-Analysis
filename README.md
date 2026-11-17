# Hospital Data Analysis

A beginner-friendly exploratory data analysis project using Python and Pandas to examine hospital admissions, patient demographics, medical conditions, insurance coverage, billing, and emergency demand.

> **Important:** This is an exploratory analysis of a dataset, not medical advice or a clinical decision-making tool. Please check the source and permitted use of the data before using it elsewhere.

## Project files

| File | Description |
| --- | --- |
| [`healthcare_dataset.csv`](healthcare_dataset.csv) | Source dataset used by the notebook. |
| [`main.ipynb`](main.ipynb) | Data loading, quality checks, cleaning, analysis, and visualizations. |
| [`Hospital_analytics_dashboard.html`](Hospital_analytics_dashboard.html) | Interactive HTML dashboard with the main results and summary tables. |
| [`LICENSE`](LICENSE) | MIT License. |

## Preview the dashboard

Open [`Hospital_analytics_dashboard.html`](Hospital_analytics_dashboard.html) in a browser. To run it locally, download or clone the repository and open the file, or start a small local web server from the project directory:

```bash
python -m http.server 8000
```

Then visit <http://localhost:8000/Hospital_analytics_dashboard.html>. The dashboard loads Chart.js from a CDN, so an internet connection is needed for its charts to display. The dashboard is a prebuilt summary; it does not load or filter individual patient rows from the CSV.

## Dataset overview

The CSV contains **55,500 rows and 15 columns**. The fields describe patient demographics and admission records, including age, gender, blood type, medical condition, admission and discharge dates, hospital, insurance provider, billing amount, admission type, medication, and test results. The source data has no missing values reported by the notebook.

The notebook identifies **534 duplicate rows** and removes them, leaving **54,966 records**. It also standardizes patient-name capitalization, replaces negative billing values with the dataset's original mean billing amount, converts dates to datetime values, and calculates length of stay. After the two derived date/length-of-stay fields are added, the cleaned data has 17 columns.

## Questions explored

- How are admissions distributed across the listed medical conditions?
- How is the patient population distributed among insurance providers?
- How do average billing amounts change over time?
- How many admissions are marked as emergency, and how do emergency counts vary by calendar month?
- What patterns appear in billing for older patients and in high-billing records?
- How many emergency records have abnormal test results?

## Headline findings

The figures below summarize the results already included in the notebook and dashboard. They describe this dataset only and should not be treated as evidence of clinical outcomes or causes.

- **54,966** records remain after duplicate removal.
- The six conditions are represented in similar numbers: Arthritis has the most records (**9,218**) and Asthma the fewest (**9,095**).
- The five insurance providers have similar record counts; Cigna is the most common (**11,139**).
- The dashboard reports an average billing amount of **25,594.54** and an average patient age of **51.54**.
- The dashboard summarizes **18,102** emergency admissions and **6,038** emergency records with abnormal test results.
- **5,497** records are flagged as high-cost (above the 90th percentile threshold used in the analysis).

## Run the notebook

### 1. Get the project files

```bash
git clone https://github.com/Rutvikkihla/Hospital-Data-Analysis.git
cd Hospital-Data-Analysis
```

You can also download the repository as a ZIP from GitHub and open a terminal in the extracted folder.

### 2. Create and activate a Python environment (recommended)

```bash
python -m venv .venv
```

Activate it on macOS/Linux:

```bash
source .venv/bin/activate
```

Activate it on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install the notebook dependencies

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib seaborn plotly
```

### 4. Start Jupyter and run the analysis

```bash
jupyter notebook
```

In the browser tab that opens, select `main.ipynb` and run the cells from top to bottom. Keep `healthcare_dataset.csv` in the same project directory so the notebook can read it. If you use JupyterLab instead, install it with `python -m pip install jupyterlab` and start it with `jupyter lab`.

## Analysis workflow

1. Load the CSV with Pandas and inspect its shape, columns, data types, and summary statistics.
2. Check missing values and duplicate rows.
3. Remove duplicate records and standardize patient-name capitalization.
4. Handle negative billing values as described in the notebook.
5. Convert admission and discharge dates to datetime values and calculate length of stay.
6. Group records to answer the analysis questions and create visualizations.
7. Review the interactive dashboard for a browsable summary of selected aggregate results.

## Tools

- **Python** for the analysis
- **Pandas** for loading, cleaning, and grouping tabular data
- **NumPy**, **Matplotlib**, **Seaborn**, and **Plotly** for calculations and visualizations in the notebook
- **Chart.js** for charts in the standalone HTML dashboard (loaded from a CDN)

## Notes and limitations

- The dashboard contains precomputed aggregate results from the notebook; it is not connected to the CSV and does not provide patient-level search.
- Re-run the notebook after changing the CSV if you want to update the analysis. The existing dashboard will not update automatically.
- The notebook replaces negative billing values with the original dataset mean. This choice affects downstream billing summaries and should be reconsidered for a different dataset or use case.
- The dataset's provenance and whether its records are synthetic or de-identified are not established by this repository. Do not assume it is suitable for real-world clinical or operational decisions.
- Findings are descriptive associations in this dataset; they do not establish causation or represent every hospital or patient population.

## License

This project is released under the [MIT License](LICENSE).
