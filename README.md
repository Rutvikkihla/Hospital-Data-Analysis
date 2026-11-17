# Hospital Data Analysis

A practical healthcare analytics project that cleans hospital patient data, answers business questions with Python, and presents the results in an interactive HTML dashboard.

## Table of Contents

- [Project Overview](#project-overview)
- [Repository Structure](#repository-structure)
- [Dataset Description](#dataset-description)
- [Analysis Steps](#analysis-steps)
- [Key Findings](#key-findings)
- [HTML Dashboard](#html-dashboard)
- [How to Run the Project](#how-to-run-the-project)
- [Tools Used](#tools-used)
- [Important Notes](#important-notes)

## Project Overview

This project loads a healthcare dataset, cleans it, adds useful columns, and studies patient conditions, billing, insurance coverage, emergency admissions and length of stay.

It answers questions such as:

- Which medical conditions appear most often?
- Which insurance providers cover the most patients?
- How do billing amounts change over time?
- What is the pattern of emergency admissions by month?
- Which high-cost or abnormal cases may need review?

The analysis is written in Python with pandas, and the findings are summarized in a dashboard you can open in any browser.

### Why this project is useful

- Practice data cleaning and exploratory data analysis (EDA)
- Understand healthcare operations data
- Build a dashboard-style business summary from raw data
- Explore patterns in patient records for reporting and decision support

## Repository Structure

```
Hospital-Data-Analysis/
├── healthcare_dataset.csv                # Raw hospital dataset
├── main.ipynb                            # Notebook with analysis and charts
├── Hospital_analytics_dashboard.html     # Interactive HTML dashboard
├── README.md                             # Project documentation
├── LICENSE                               # MIT License
└── .gitignore                            # Repo configuration (optional)
```

| File | Purpose |
|------|---------|
| `main.ipynb` | Loads the data, checks quality, cleans it, groups and summarizes fields, plots charts and answers the business questions |
| `healthcare_dataset.csv` | Source data used in the analysis |
| `Hospital_analytics_dashboard.html` | Dashboard that shows the findings visually and opens directly in a browser |
| `README.md` | This guide |

## Dataset Description

The original file has **55,500 rows and 15 columns**, with no missing values and **534 duplicate rows**.

| Group | Columns |
|-------|---------|
| Patient | Name, Age, Gender, Blood Type |
| Medical | Medical Condition, Medication, Test Results |
| Admission | Date of Admission, Discharge Date, Admission Type, Room Number |
| Hospital and billing | Doctor, Hospital, Insurance Provider, Billing Amount |

## Analysis Steps

### Step 1: Load and inspect
Read the CSV, then check the first rows, data types, shape, summary statistics, missing values and duplicates.

### Step 2: Clean the data
1. **Remove duplicates.** 534 rows dropped, leaving 54,966 records.
2. **Fix names.** Extra spaces removed and capitalization made consistent (`DaNnY sMitH` becomes `Danny Smith`).
3. **Fix negative billing amounts.** Values below zero replaced with the column mean.
4. **Convert dates.** Admission and discharge columns converted to datetime format.

### Step 3: Create new columns
- `days_stayed`: discharge date minus admission date
- `admission_month`: month of admission, used for the cost trend

The cleaned data has **54,966 rows and 17 columns**.

### Step 4: Answer the business questions

| Question | Method | Result |
|----------|--------|--------|
| Which medical condition affects the most patients? | Count patients per condition | Arthritis is highest (9,218), Asthma lowest (9,095) |
| How is patient age distributed? | Average age and histogram | Average age is about 51.5 |
| How has average treatment cost changed over time? | Average billing per admission month | Overall average is about 25,594.54 across 61 months |
| Is there a link between age and treatment cost? | Average cost for ages 60 and over, plus scatter plot | Seniors average about 25,563.59, close to the overall average |
| Which insurance providers cover the most patients? | Count patients per provider | Cigna is highest (11,139), Aetna lowest (10,822) |

### Step 5: Extra business questions

| Question | Result |
|----------|--------|
| How many emergency admissions occur each month? | 18,102 in total, with July highest (1,573) and February lowest (1,452) |
| Who are the high-cost patients? | 5,497 patients have billing above the 90th percentile |
| Which emergency cases have abnormal test results? | 6,038 cases flagged for review |

Monthly emergency counts add up across all years, so they show the pattern by calendar month.

## Key Findings

- The dataset has 55,500 records before cleaning and **54,966** after removing duplicates.
- Medical conditions are spread evenly, between 9,095 and 9,218 patients each.
- Insurance coverage is split across five providers, with shares between 19.7% and 20.3%.
- Average billing stays in a narrow band around 25,594.54 from May 2019 to May 2024.
- Emergency admissions happen all year, with about 8% between the highest and lowest month.
- 6,038 emergency cases (about a third of all emergencies) have abnormal results and may need review.
- High-cost records can be found with a billing threshold: 5,497 patients (10%) sit above the 90th percentile.

These findings describe patterns in the data. They are not clinical or medical guidance.

## HTML Dashboard

`Hospital_analytics_dashboard.html` turns the notebook results into one interactive page.

### Sections

| Section | What it shows |
|---------|---------------|
| Executive Summary | The main findings in a few lines |
| KPIs | Clean records, average billing, average age, top condition, top insurer, emergency admissions and more |
| Patients | Patients by condition (bar chart) and insurance provider (donut chart) |
| Billing | Average billing by admission month (line chart) |
| Emergency | Emergency admissions by calendar month, plus high-cost and abnormal-case counts |
| Insights | Each insight with what the data shows, why it matters and an action to consider |
| Data Explorer | Searchable, sortable tables behind the charts |
| Conclusion | A short wrap-up |

### Features

- Click bars and donut slices to see details
- Sort the condition chart and pick a date range on the billing chart
- Search, sort and page through tables, then download them as CSV
- Save any chart as PNG or view it fullscreen
- Presentation mode, print layout and a Reset all button

### How to open it

1. Open the repository folder on your computer.
2. Double-click `Hospital_analytics_dashboard.html`, or serve it locally:
   ```bash
   python -m http.server 8000
   ```
   Then open `http://localhost:8000/Hospital_analytics_dashboard.html`.

> **Note:** The dashboard loads Chart.js from a CDN, so internet access is required for the charts to appear.

### Limits

- The dashboard uses summarized results from the notebook, so it has no patient-level filters (such as gender or hospital) and no table of individual records.
- The age histogram and age-versus-billing scatter plot stay in the notebook only.

## How to Run the Project

### Step 1: Clone the repository
```bash
git clone https://github.com/Rutvikkihla/Hospital-Data-Analysis.git
cd Hospital-Data-Analysis
```

### Step 2: Create a virtual environment (recommended)

Windows:
```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:
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
Open `main.ipynb` and run all cells from top to bottom.

## Tools Used

- Python
- Pandas and NumPy
- Matplotlib, Seaborn and Plotly
- Jupyter Notebook
- HTML, CSS, JavaScript and Chart.js (dashboard)

## Important Notes

- This project is for educational and exploratory analysis.
- It does not replace professional medical advice or decision-making.
- Findings are based on dataset patterns and should not be treated as clinical conclusions without further validation.
- Negative billing values were replaced with the column mean, as in the notebook.

## Author

Rutvik Kihla
