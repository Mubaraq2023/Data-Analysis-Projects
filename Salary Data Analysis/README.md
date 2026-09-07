# Salary Data Analysis

Exploratory Data Analysis of a salary dataset, uncovering pay trends across job roles, cities, companies and company ratings.

## Overview

This project is a Jupyter notebook that cleans and analyzes a salary dataset. It answers common business questions like which job roles and cities pay the most, whether company rating affects salary and which companies offer the highest pay. The goal is to turn raw salary records into clear, visual insights that can support hiring, compensation or career decisions.

## Key Features

- Data Cleaning: handles missing values and checks for duplicate records
- Outlier detection and removal using the IQR (Interquartile Range) method
- Univariate Analysis of salary distribution
- Answers to 9+ business questions, including:
  - Highest-paying job roles and cities
  - Top companies in New Delhi rated 5 stars by highest and lowest salary
  - Top 5 companies by average salary
  - Job titles with the most reported salaries
  - Top-paying companies with at least 20 reported salaries
  - Relationship between company rating and salary
  - Effect of employment status (Full Time, Intern, Contractor, Trainee) on salary
  - Most common job roles
  - Salary trend across company rating levels
- A combined mini-dashboard summarizing the key findings in one view

## Tech Stack / Dependencies

- Python 3
- [Jupyter Notebook](https://jupyter.org/)
- [pandas](https://pandas.pydata.org/) — Data Loading and Manipulation
- [numpy](https://numpy.org/) — Numerical Operations
- [matplotlib](https://matplotlib.org/) — Visualization
- [seaborn](https://seaborn.pydata.org/) — Statistical Visualization

## Installation / Setup

1. Clone or download this project.
2. Install the required packages:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. Place the dataset CSV file in the project's root folder (see [Dataset](#dataset) below).
4. Launch the notebook:

   ```bash
   jupyter notebook salary_data_analysis.ipynb
   ```

## Usage

Run the notebook cells in order from top to bottom. The notebook is organized into these stages:

```text
1. Import Dependencies
2. Load Dataset
3. Basic Dataset Understanding
4. Data Cleaning
5. Outlier Detection and Removal
6. Univariate Analysis
7. Answering Business Questions (Q1–Q9)
8. Mini Dashboard
```

Example: loading the dataset and previewing it

```python
import pandas as pd

df = pd.read_csv("Salary_Dataset_DSL.csv")
df.head()
```

Example: finding the highest-paying job roles

```python
jobrole_avg_salary = (
    df.groupby("Job Roles")["Salary"]
    .mean()
    .sort_values(ascending=False)
    .head(10)
)
```

## Dataset

The notebook expects a CSV file named `Salary_Dataset_DSL.csv` in the same folder, with (at least) the following columns:

- `Company Name`
- `Job Title`
- `Job Roles`
- `Salary`
- `Salaries Reported`
- `Rating`
- `Location`
- `Employment Status`

## Configuration

No environment variables or config files are required. The only setup needed is placing the dataset CSV in the same directory as the notebook (or updating the file path in the "Load Dataset" cell).

## Project Structure

```text
.
├── salary_data_analysis.ipynb   # Main analysis notebook
├── Salary_Dataset_DSL.csv       # Dataset
└── README.md
```

## Contributing

This is a personal/exploratory analysis project, but improvements are welcome:

1. Fork the repository
2. Create a new branch for your change
3. Make your edits to the notebook
4. Open a pull request with a short description of what changed
