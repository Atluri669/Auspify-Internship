# Netflix Content Type Analysis Dashboard

## Overview
This project analyzes the Netflix content catalog to compare the distribution of Movies and TV Shows in the dataset. The analysis helps understand which content type dominates the platform and how heavily the catalog is skewed toward one category.

## Dataset
- File: `DATA/Netflix_cleaned.csv`
- Records analyzed: 8,790
- Columns reviewed: title, type, release year, country, rating, duration, and category metadata

## Key Findings
| Content Type | Count | Percentage |
|---|---:|---:|
| Movie | 6,126 | 69.69% |
| TV Show | 2,664 | 30.31% |

- Total content records: 8,790
- Movies are the dominant category by a count difference of 3,462 titles.
- Movie share exceeds TV Shows by 39.39 percentage points.

## Interpretation
The dataset is heavily skewed toward Movies, with nearly 70% of all entries classified as Movies. TV Shows account for about 30% of the catalog. This indicates that Netflix's catalog in this dataset is more movie-oriented than TV-show-oriented.

## Project Structure
- `DATA/` — source dataset files
- `NOTEBOOK/` — Jupyter notebook and analysis outputs
- `NOTEBOOK/reports/` — summary CSV files generated from the analysis
- `NOTEBOOK/*.png` — visual charts showing distribution and percentage breakdown

## Generated Outputs
- `NOTEBOOK/content_type_analysis.ipynb`
- `NOTEBOOK/reports/content_type_summary.csv`
- `NOTEBOOK/reports/content_type_analysis_report.csv`
- `NOTEBOOK/content_type_distribution.png`
- `NOTEBOOK/content_type_count.png`
- `NOTEBOOK/content_type_percentage.png`

## Conclusion
Movies dominate the Netflix content catalog in this dataset, making up the majority of available entries. The analysis demonstrates a clear content preference toward Movies compared with TV Shows.
