# Netflix Business Insights & Analytics

An end-to-end data analytics and business intelligence project exploring
the Netflix content catalog using **Python, Pandas, NumPy, Matplotlib,
Seaborn, and Power BI**.

## Project Overview

This project analyzes a Netflix catalog dataset containing information
about movies and TV shows. It explores catalog composition, release
patterns, content ratings, genres, production countries, movie runtimes,
and TV show seasons.

Python is used for data preparation and exploratory data analysis (EDA),
while Power BI is used to build interactive dashboards.

> **Scope note:** The dataset contains catalog metadata. It does not
> include viewing hours, subscribers, revenue, profit, or customer
> engagement. Findings therefore describe catalog patterns, not proven
> audience popularity or financial performance.

## Business Objectives

1.  Understand the distribution of Movies and TV Shows.
2.  Identify frequently represented genres and content ratings.
3.  Explore country-wise content representation.
4.  Examine release-year and Netflix addition-year trends.
5.  Analyze movie runtimes and TV show season counts.
6.  Build interactive Power BI dashboards.
7.  Present evidence-based business recommendations.

## Dataset

**Input file:** `Netflix_cleaned(3).csv`\
**Expected size:** 8,790 rows and 10 columns.

  Column           Description
  ---------------- ------------------------------------------------
  `show_id`        Unique identifier for a title
  `type`           Movie or TV Show
  `title`          Title name
  `director`       Director information
  `country`        Country or countries associated with the title
  `date_added`     Date the title was added to Netflix
  `release_year`   Original release year
  `rating`         Content maturity rating
  `duration`       Movie runtime or TV show season count
  `listed_in`      Genre/category labels

The notebook produces `Netflix_Final_Cleaned.csv`.

## Tools and Technologies

-   Python
-   Pandas and NumPy
-   Matplotlib and Seaborn
-   Jupyter Notebook
-   Power BI Desktop
-   DAX
-   Power Query

## Repository Structure

``` text
Netflix-Business-Insights/
├── Dataset/
│   ├── Netflix_cleaned(3).csv
│   └── Netflix_Final_Cleaned.csv
├── Notebooks/
│   └── Netflix_Business_Insights_Report.ipynb
├── Visualizations/
│   ├── content_type.png
│   ├── top_countries.png
│   ├── top_genres.png
│   ├── content_ratings.png
│   ├── release_trends.png
│   └── movie_duration.png
├── PowerBI/
│   └── Netflix_Business_Insights.pbix
├── Reports/
│   └── Netflix_Business_Insights_Report.pdf
└── README.md
```

*This is a suggested structure. Keep only files that you have actually
created.*

## Analysis Workflow

### 1. Data loading and inspection

-   Load the CSV file with Pandas.
-   Inspect records, columns, data types, and dimensions.
-   Check missing values and duplicates.

### 2. Data cleaning

-   Remove duplicate records where appropriate.
-   Standardize missing-value placeholders such as `Not Given`.
-   Normalize country text carefully.
-   Parse `date_added` as a date and extract year/month.
-   Extract numeric duration and duration unit.
-   Validate changes against the original data.

### 3. Exploratory Data Analysis

-   Movies versus TV Shows
-   Titles by release year
-   Titles added by year
-   Country representation
-   Genre distribution
-   Content ratings
-   Movie runtime distribution
-   TV Shows by number of seasons

### 4. Dashboard development

Create three Power BI report pages: 1. **Executive Overview** ---
catalog KPIs, Movies versus TV Shows, countries, genres, and addition
trends. 2. **Content Analysis** --- ratings, genres, movie runtimes, and
TV show seasons. 3. **Country and Trend Analysis** --- country
distribution, release trends, addition trends, and content type by
country.

## Key Findings

The supplied dataset analysis reported the following catalog-level
results:

  Metric                                                                      Finding
  ------------------------------------------------------ ----------------------------
  Total titles                                                                  8,790
  Movies                                                                        6,126
  TV Shows                                                                      2,664
  Movies as a share of titles                                                  69.69%
  TV Shows as a share of titles                                                30.31%
  Average movie duration                                   Approximately 99.6 minutes
  Most frequent content rating                                                  TV-MA
  Most frequent release year                                                     2018
  Highest Netflix addition year in the analyzed period                           2019

Recalculate these metrics from the final cleaned dataset before
publication. Country and genre counts depend on how multi-country and
multi-genre records are split and counted.

## Power BI Dashboards

### Dashboard 1 --- Executive Overview

Suggested visuals: - Total Titles, Total Movies, and Total TV Shows KPI
cards - Movie and TV Show percentage cards - Content type donut chart -
Top 10 countries bar chart - Top 10 genres bar chart - Titles added by
year line chart

### Dashboard 2 --- Content Analysis

Suggested visuals: - Content ratings bar chart - Movie duration
histogram - TV show seasons column chart - Genre distribution chart -
Rating by content type chart

### Dashboard 3 --- Country and Trend Analysis

Suggested visuals: - Country distribution map (after validating country
fields) - Top 10 countries bar chart - Titles by release year - Titles
added by year - Country versus content type matrix

### Suggested DAX Measures

Assuming the main table is named `Netflix`:

``` dax
Total Titles =
DISTINCTCOUNT(Netflix[show_id])

Total Movies =
CALCULATE(
    [Total Titles],
    Netflix[type] = "Movie"
)

Total TV Shows =
CALCULATE(
    [Total Titles],
    Netflix[type] = "TV Show"
)

Movie Percentage =
DIVIDE([Total Movies], [Total Titles], 0)

TV Show Percentage =
DIVIDE([Total TV Shows], [Total Titles], 0)

Average Movie Duration =
CALCULATE(
    AVERAGE(Netflix[duration_value]),
    Netflix[type] = "Movie"
)

Average TV Seasons =
CALCULATE(
    AVERAGE(Netflix[duration_value]),
    Netflix[type] = "TV Show"
)
```

**Important:** Confirm the exact values in the `type` column before
using these measures. If the dataset uses `Tv Show`, replace `TV Show`
in the DAX filters with that exact value.

## How to Run the Project

### Prerequisites

-   Python 3.10 or later
-   Jupyter Notebook or JupyterLab
-   Power BI Desktop (for dashboards)

### 1. Clone the repository

``` bash
git clone https://github.com/Atluri669/Netflix-Business-Insights.git
cd Netflix-Business-Insights
```

Replace the URL if you publish the project under a different repository
name.

### 2. Create a virtual environment

**Windows:**

``` bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**

``` bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

``` bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Start Jupyter

``` bash
jupyter notebook
```

Open `Notebooks/Netflix_Business_Insights_Report.ipynb`.

### 5. Load the dataset

If the notebook is inside `Notebooks/` and the CSV is inside `Dataset/`:

``` python
import pandas as pd

df = pd.read_csv("../Dataset/Netflix_cleaned(3).csv")
```

Save the cleaned output:

``` python
df.to_csv("../Dataset/Netflix_Final_Cleaned.csv", index=False)
```

Run the notebook cells in order.

### 6. Open the Power BI report

After creating the `.pbix` file, open
`PowerBI/Netflix_Business_Insights.pbix`. Refresh the data source if the
dataset location has changed.

## Data Quality and Limitations

-   Placeholder text may represent missing values.
-   Country and genre fields may contain multiple values in one record.
-   Split multi-value fields into rows when counting individual
    countries or genres.
-   `date_added` and `release_year` describe different events.
-   The latest year may be incomplete.
-   Catalog counts do not measure views, watch time, satisfaction, or
    profitability.
-   Validate country names before using a geographic map.

## Future Improvements

-   Add viewing-hours and audience-engagement data, if available.
-   Add subscription and revenue data for financial analysis.
-   Build a time-based content acquisition dashboard.
-   Compare regional catalog and genre mixes.
-   Add automated data-quality checks.
-   Publish the Power BI report through an appropriate workspace.
-   Add screenshots of completed dashboards to the repository.

## Author

**Atluri Vishnu Vardhan**\
**Project:** Netflix Business Insights & Analytics\
**Focus:** Data Analytics \| Business Intelligence \| Python \| SQL \|
Power BI

-   GitHub: https://github.com/Atluri669

------------------------------------------------------------------------

*For educational and portfolio purposes. Validate findings against the
final cleaned dataset before using them in business decisions.*
