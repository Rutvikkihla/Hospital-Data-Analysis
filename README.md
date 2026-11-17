# Hospital Data Analysis

A clear and practical healthcare analytics project focused on understanding hospital patient data, identifying key patterns, and exploring operational insights using Python, pandas, and data visualization.

This project loads a healthcare dataset, performs data cleaning, derives useful features, and analyzes trends in patient conditions, billing, insurance coverage, emergency admissions, and patient stay duration.

## Project Overview

Hospital Data Analysis is designed to help users explore real-world-style hospital data and answer business questions such as:

- Which medical conditions appear most often?
- Which insurance providers cover the most patients?
- How do billing amounts vary over time?
- What is the pattern of emergency admissions by month?
- Which high-cost or abnormal cases may need review?

The notebook is written in Python and uses the pandas library for data cleaning and analysis. The result is summarized in an interactive HTML dashboard that presents the key findings in a simple, visual way.

## Why this project matters

This repository is useful for:

- learning data cleaning and exploratory data analysis (EDA)
- understanding healthcare operations data
- practicing Python-based data analysis workflows
- building dashboard-style business summaries from raw data
- exploring patterns in patient records for reporting and decision support

## Repository Structure

```text
Hospital-Data-Analysis/
├── healthcare_dataset.csv        # Raw hospital dataset
├── main.ipynb                   # Python notebook with analysis and visualizations
├── Hospital_analytics_dashboard.html  # HTML dashboard preview
├── README.md                    # Project documentation
├── LICENSE                      # MIT License
└── .gitignore                   # Optional repo configuration (if present)
```

## Dataset Description

The dataset contains hospital-related records with columns such as:

- Name
- Age
- Gender
- Blood Type
- Medical Condition
- Date of Admission
- Doctor
- Hospital
- Insurance Provider
- Billing Amount
- Room Number
- Admission Type
- Discharge Date
- Medication
- Test Results

The project performs the following data-quality steps:

- removes duplicate rows
- fixes inconsistent text formatting in names
- replaces negative billing values with the dataset mean
- converts date columns to datetime format
- calculates `days_stayed` based on admission and discharge dates

## Key Findings from the Analysis

The project identifies several business insights, including:

- The dataset contains over 55,000 patient records before cleaning.
- After dropping duplicates and fixing invalid values, about 54,966 rows remain.
- Medical conditions are spread relatively evenly across the dataset.
- Insurance coverage is distributed across multiple providers.
- Average billing remains fairly stable over time.
- Emergency admissions occur throughout the year, with some monthly variation.
- A meaningful number of emergency cases have abnormal results and may require review.
- High-cost records can be identified using billing thresholds.

These findings are descriptive and intended for exploratory analysis, not as clinical or medical guidance.

## Files Included

### 1. `main.ipynb`
This is the main analysis notebook.

It includes:

- loading the dataset
- checking null values and duplicates
- data cleaning
- grouping and summarizing fields
- plotting charts and graphs
- answering key business questions

### 2. `healthcare_dataset.csv`
This file is the source dataset used in the analysis.

### 3. `Hospital_analytics_dashboard.html`
This file is an HTML preview of the healthcare analytics dashboard. It summarizes the project findings in an easy-to-read visual format and can be opened directly in a browser.

### 4. `README.md`
This documentation explains the project clearly for anyone who wants to understand the workflow and run it locally.

## HTML Dashboard Preview

A ready-made preview is already included:

- `Hospital_analytics_dashboard.html`

To view it:

1. Open the repository folder in your local system.
2. Double-click the file `Hospital_analytics_dashboard.html`, or
3. Serve it locally using a simple Python HTTP server:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/Hospital_analytics_dashboard.html
```

> Note: The dashboard loads Chart.js from a CDN, so internet access is required for full rendering in the browser.

## How to Run the Project

### Step 1: Clone the repository

```bash
git clone https://github.com/Rutvikkihla/Hospital-Data-Analysis.git
cd Hospital-Data-Analysis
```

### Step 2: Create a virtual environment (recommended)

On Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

On macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

### Step 3: Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install pandas numpy matplotlib seaborn plotly jupyter
```

### Step 4: Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open `main.ipynb` and run all cells in order.

## Notebook Workflow

The notebook follows a standard data analysis flow:

1. Load the CSV file
2. Inspect the dataset structure
3. Check for null values and duplicate rows
4. Clean the dataset
5. Fix inconsistent values and dates
6. Add derived fields such as `days_stayed`
7. Analyze patterns and trends
8. Create charts and summary metrics
9. Summarize insights in the dashboard

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Plotly
- Jupyter Notebook
- HTML/CSS/JavaScript for the dashboard preview

## Example Questions the Project Answers

- Which department or case type has the highest patient volume?
- Are there patterns in emergency admissions by month?
- What is the overall spread of billing amounts?
- Which insurance providers are most common?
- Are abnormal test results concentrated in certain groups?

## Important Notes

- This project is for educational and exploratory analysis.
- It is not intended to replace professional medical advice or decision-making.
- The data is used for analysis and reporting purposes only.
- Findings are based on dataset patterns and should not be interpreted as clinical conclusions without additional validation.

## License

This project is licensed under the MIT License.

See the [LICENSE](LICENSE) file for full details.

## Contact / Repository

Repository: https://github.com/Rutvikkihla/Hospital-Data-Analysis

If you want, I can also help you create a more polished landing-page style HTML preview or a GitHub-ready project banner for this repository.
