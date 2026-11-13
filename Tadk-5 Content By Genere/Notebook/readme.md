import pypandoc

readme = r"""# Netflix Content Rating & Genre Analysis

## Project Overview

This project explores the Netflix titles dataset to understand its content-rating distribution, most common genres, differences between Movies and TV Shows, and approximate audience segments.

The analysis uses Python for data cleaning, exploratory data analysis (EDA), visualization, and report generation. It includes both static charts (Matplotlib and Seaborn) and interactive charts (Plotly).

## Project Objectives

- Analyze the distribution of Netflix content ratings.
- Identify the most common genres on Netflix.
- Compare ratings across Movies and TV Shows.
- Explore genre patterns by content type.
- Group rating categories into approximate audience segments.
- Create static and interactive visualizations.
- Export summary tables and cleaned data to an Excel workbook.

## Dataset

**File:** `Netflix_cleaned(2).csv`

The dataset used for this project contains **8,790 rows and 10 columns**.

| Column | Description |
|---|---|
| `show_id` | Unique Netflix title identifier |
| `type` | Content type: Movie or TV Show |
| `title` | Title of the movie or TV show |
| `director` | Director name(s), where available |
| `country` | Country or countries associated with the title |
| `date_added` | Date the title was added to Netflix |
| `release_year` | Original release year |
| `rating` | Content rating |
| `duration` | Movie runtime or number of TV seasons |
| `listed_in` | Genre/category labels |

> The dataset is used for learning and portfolio analysis. Results describe the supplied dataset, not necessarily Netflix's current catalogue.

## Technologies Used

- **Python**
- **Pandas** – data loading, cleaning, grouping, and analysis
- **NumPy** – numerical operations
- **Matplotlib** – static visualizations
- **Seaborn** – statistical visualizations
- **Plotly** – interactive charts and dashboard-style visuals
- **OpenPyXL** – Excel export support
- **Jupyter Notebook / JupyterLab** – development environment

## Project Workflow

1. Load the CSV dataset with Pandas.
2. Inspect the shape, columns, missing values, and duplicates.
3. Clean selected fields and convert `date_added` to a datetime value.
4. Analyze content-rating counts and percentages.
5. Split the comma-separated `listed_in` values to count individual genres.
6. Compare rating distributions for Movies and TV Shows.
7. Create approximate audience segments from content-rating labels.
8. Compare genres across content types.
9. Explore rating-versus-genre patterns with a heatmap.
10. Build interactive Plotly visualizations.
11. Generate summary insights and export analysis tables to Excel.

## Key Analyses and Visualizations

### 1. Content Rating Analysis
- Count of titles in each rating category
- Percentage share of each rating
- Bar chart and pie chart
- Interactive Plotly bar chart

### 2. Genre Analysis
- Frequency of individual genres
- Top 10 most common genres
- Static and interactive genre charts

### 3. Movies vs TV Shows
- Overall content-type distribution
- Rating counts by content type
- Rating percentages within each content type

### 4. Audience Segmentation
The notebook maps selected rating labels into broad, approximate groups:

- Kids
- General Audience
- Family
- Teenagers
- Adults
- Not Classified

These are analytical groupings based on rating labels. They do **not** represent verified viewer ages or actual audience demographics. Missing or unrecognized rating labels should remain separate from classified groups.

### 5. Genre and Rating Relationship
- Cross-tabulation of genres and ratings
- Heatmap of the most common genres against rating categories

### 6. Interactive Dashboard
A Plotly dashboard-style figure combines:
- Content-type distribution
- Top genres
- Rating distribution
- Audience-segment distribution

## Getting Started

### 1. Clone or download the project

```bash
git clone https://github.com/your-username/netflix-content-rating-genre-analysis.git
cd netflix-content-rating-genre-analysis
```

Replace the example repository URL with your own GitHub repository URL.

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn plotly openpyxl jupyter
```

### 3. Add the dataset

Place `Netflix_cleaned(2).csv` in the project folder, or update the CSV path in the notebook to match its location.

### 4. Start Jupyter

```bash
jupyter notebook
```

Open the project notebook and run the cells from top to bottom.

## Expected Output Files

The analysis notebook creates:

- `Netflix_Content_Rating_Genre_Analysis.xlsx` – Excel workbook containing cleaned data and analysis tables.
- Static charts displayed in the notebook.
- Interactive Plotly charts displayed in the notebook.

To keep charts as image files in your repository, save them explicitly from the notebook using `plt.savefig()` for Matplotlib charts or `fig.write_html()` for Plotly charts.

## Suggested Repository Structure

```text
netflix-content-rating-genre-analysis/
│
├── data/
│   └── Netflix_cleaned(2).csv
│
├── notebooks/
│   └── Netflix_Content_Rating_Genre_Analysis.ipynb
│
├── outputs/
│   └── Netflix_Content_Rating_Genre_Analysis.xlsx
│
├── README.md
└── requirements.txt
```

You can create a `requirements.txt` file with:

```text
pandas
numpy
matplotlib
seaborn
plotly
openpyxl
jupyter
```

## Key Business Questions

- Which content ratings occur most frequently in the dataset?
- Which genres have the highest title counts?
- Does the dataset contain more Movies or TV Shows?
- How do rating distributions differ between Movies and TV Shows?
- Which genres are most represented within each content type?
- How is the catalogue distributed across the approximate rating-based audience groups?

## Important Notes and Limitations

- A title can belong to multiple genres. Genre counts therefore count each title once for every listed genre; genre totals can exceed the number of titles.
- The audience segments are simplified interpretations of rating labels and are not demographic measurements.
- `Not Rated` and `Not Classified` should not be interpreted as an audience category.
- The dataset may contain missing values, inconsistent text, or multiple countries/directors in a single field. Interpret results in light of the cleaning steps used.
- This is a descriptive analysis. It does not establish why Netflix selected particular titles or prove viewer preferences.

## Skills Demonstrated

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Pandas grouping, aggregation, and cross-tabulation
- Feature exploration
- Data visualization and dashboard design
- Interactive reporting with Plotly
- Business insight generation
- Exporting analysis results to Excel

## Author

**Your Name**

Add your name, LinkedIn profile, and GitHub profile here before publishing the project.

## License

This project is intended for educational and portfolio purposes. Check the dataset's original source and terms before redistributing the data.
"""

output_path = "/mnt/data/README_Netflix_Content_Rating_Genre_Analysis.md"
pypandoc.convert_text(
    readme,
    "md",
    format="md",
    outputfile=output_path,
    extra_args=["--standalone"]
)

print(f"README created: {output_path}")
