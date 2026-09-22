# U.S. Emissions Analytics with Databricks

An end-to-end data analytics project built using **Databricks SQL** to analyze greenhouse gas (GHG) emissions across the United States and present the results through an interactive Databricks dashboard.

## Project Overview

This project analyzes U.S. greenhouse gas emissions data using SQL in Databricks. The analysis focuses on geographic emission patterns, emissions per person, state-level totals, top-emitting regions, and the contribution of the highest-emitting states to overall emissions.

The final results are presented through an interactive Databricks dashboard to make the findings easier to explore and understand.

## Tools & Technologies

- Databricks
- Databricks SQL
- Databricks AI/BI Dashboards
- SQL
- Data Visualization
- Git & GitHub
- EPA Emissions Data

## Key Analysis

The project focuses on:

- Mapping greenhouse gas emissions geographically using latitude and longitude
- Calculating emissions per person
- Aggregating total emissions by state
- Ranking states by total emissions
- Calculating the contribution of the top 10 states to overall U.S. emissions
- Identifying the highest-emitting counties
- Comparing population with emissions per person

## Dashboard Visualizations

The Databricks dashboard includes:

- Geographic map of U.S. emissions
- Emissions vs. population scatter plot
- State-level emissions breakdown
- Top 10 states' contribution to total emissions
- Top-emitting counties bar chart

- Preview of the dashboard
- <img width="1483" height="667" alt="image" src="https://github.com/user-attachments/assets/5ad29b32-fd72-4e40-b9c0-42cdda45e7e2" />


## Repository Structure

```text
US-Emissions-Analytics-with-Databricks/
│
├── README.md
│
├── data/
│   └── emissions_data.csv
│
├── sql/
│   └── emissions_analysis.sql
│
└── dashboard/
    └── emissions_dashboard.lvdash.json
```
## Dataset

The project uses U.S. greenhouse gas emissions data containing fields such as:

- County and state name
- State abbreviation
- Population
- Latitude
- Longitude
- GHG emissions in million tons of CO2 equivalent

The project is based on 2023 emissions data from the U.S. Environmental Protection Agency (EPA).

## Data Preparation

The dataset required several transformations before analysis, including:

- Cleaning formatted numeric values
- Converting emissions values into numeric format
- Converting population values into numeric format
- Handling division-by-zero cases
- Aggregating emissions by state
- Ranking states and counties based on emissions

## Questions Explored

This project explores questions such as:

- Which U.S. regions have the highest greenhouse gas emissions?
- Which counties have the highest emissions per person?
- Which states contribute the most to total emissions?
- What percentage of total emissions comes from the top 10 states?
- How does population relate to emissions per person?
- Where are major emission concentrations located geographically?

## Running the Project

1. Upload the emissions dataset to Databricks.
2. Create or load the `emissions_data` table.
3. Run the SQL analysis files from the `sql/` folder.
4. Open or import the Databricks dashboard.
5. Connect the dashboard visualizations to the appropriate datasets.
6. Refresh the dashboard to view the results.

## Skills Demonstrated

- SQL data cleaning and transformation
- Data aggregation and ranking
- Common Table Expressions (CTEs)
- Analytical calculations
- Databricks SQL
- Dashboard development
- Data visualization
- Git and GitHub version control
- Environmental data analysis

## Future Improvements

- Add year-over-year emissions comparisons
- Add filters for state and county
- Compare emissions across different sectors
- Automate data refreshes in Databricks
- Add additional environmental and demographic indicators
