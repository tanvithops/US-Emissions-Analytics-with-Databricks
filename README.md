# U.S. Emissions Analytics with Databricks
An end-to-end data engineering and analytics project built using **Databricks, Delta Lake, SQL, Unity Catalog, and Databricks AI/BI Dashboards** to analyze
greenhouse gas emissions across the United States.
The project follows the **Medallion Architecture** using Bronze, Silver, and Gold layers to ingest raw EPA emissions data, clean and standardize it, create
analytics-ready datasets, and serve the final results through an interactive dashboard.
## Project Architecture
```text
EPA Emissions CSV
        ↓
Unity Catalog Volume
        ↓
Bronze Layer
emissions.bronze.emissions_raw
        ↓
Silver Layer
emissions.silver.emissions_clean
        ↓
Gold Layer
├── emissions.gold.county_metrics
├── emissions.gold.state_emissions
└── emissions.gold.emissions_summary
        ↓
Databricks AI/BI Dashboard
```
## Tools & Technologies- Databricks- Databricks SQL- Delta Lake- Unity Catalog- Databricks AI/BI Dashboards- SQL- Git & GitHub- EPA Emissions Data- Medallion Architecture
## Dataset
The project uses 2023 U.S. greenhouse gas emissions data containing information such as:- County name- State abbreviation- Population- Latitude- Longitude- Greenhouse gas emissions- Energy-related metrics- Geographic identifiers
The source dataset contains **3,142 records**.
## Bronze Layer
The Bronze layer stores the raw EPA emissions data with minimal transformation.
The source CSV is uploaded to a Unity Catalog Volume and ingested into a Delta table:
```text
emissions.bronze.emissions_raw
```
The Bronze layer preserves the original source structure and adds ingestion metadata including:- Source file name- Ingestion timestamp
This layer acts as the raw historical source for downstream processing.
## Silver Layer
The Silver layer cleans and standardizes the raw emissions data.
The cleaned table is:
```text
emissions.silver.emissions_clean
```
Transformations include:- Standardizing column names- Converting formatted numeric values into numeric data types- Converting population values to numeric format- Converting greenhouse gas emissions to numeric format- Standardizing state and county identifiers- Cleaning geographic fields- Validating latitude and longitude- Handling invalid numeric values- Preserving ingestion metadata
Data-quality checks confirmed:
```text
Total rows:          3142
Null population:     0
Null emissions:      0
Null latitude:       0
Null longitude:      0
```
## Gold Layer
The Gold layer contains business-ready and analytics-ready tables used by the dashboard.
### County Metrics
```text
emissions.gold.county_metrics
```
Contains county-level metrics including:- Population- Latitude and longitude- Total greenhouse gas emissions
- Emissions per person- State and county identifiers
This table supports geographic mapping, county rankings, and population analysis.
### State Emissions
```text
emissions.gold.state_emissions
```
Contains state-level aggregates including:- Total state population- Total state emissions- Emissions per person- Percentage of total U.S. emissions- Emissions ranking
### Emissions Summary
```text
emissions.gold.emissions_summary
```
Contains high-level summary metrics including:- Total U.S. emissions- Combined emissions of the top 10 states- Percentage of total emissions contributed by the top 10 states
## Dashboard
The final Databricks AI/BI dashboard reads from the Gold layer instead of directly querying raw data.
Dashboard visualizations include:- Geographic distribution of greenhouse gas emissions- Population vs. emissions per person- Top states by total emissions- Top 10 states' contribution to total U.S. emissions- Top counties by total greenhouse gas emissions
This separates data engineering logic from visualization logic and keeps the dashboard focused on analytics-ready datasets.
Dashboard preview:
<img width="1718" height="769" alt="use" src="https://github.com/user-attachments/assets/1daae7d5-8950-43f1-a46a-6a4f989ab3b8" />

## Data Pipeline Flow
The complete pipeline follows:
```text
Raw EPA CSV
   ↓
Bronze
Raw Delta Table
   ↓
Silver
Cleaned and Standardized Delta Table
   ↓
Gold
Aggregated Analytics Tables
   ↓
Databricks Dashboard
```
## SQL Transformations
The repository contains separate SQL transformations for each layer:
```text
SQL Queries/
├── Bronze Transformation
├── Silver Transformation
└── Gold Transformation
```
### Bronze Transformation
Responsible for:- Reading the raw CSV- Loading the source data into Delta Lake- Preserving raw source fields- Adding ingestion metadata
### Silver Transformation
Responsible for:- Data cleaning- Data type conversion- Standardization- Data-quality validation- Preparing clean county-level records
### Gold Transformation
Responsible for:- County-level analytical metrics- Emissions-per-person calculations- State-level aggregations- State rankings- Top-10 emissions analysis- Dashboard-ready summary metrics
## Repository Structure
```text
US-Emissions-Analytics-with-Databricks/
│
├── README.md
├── Emissions_Data_2023.csv
├── Emissions Dashboard.lvdash.json
│
└── SQL Queries/
    ├── Bronze Transformation.dbquery.ipynb
    ├── Silver Transformation.dbquery.ipynb
    └── Gold Transformation.dbquery.ipynb
```
## Key Questions Explored
This project explores questions such as:- Which counties produce the highest greenhouse gas emissions?- Which states contribute the most to total U.S. emissions?- Which counties have the highest emissions per person?- What percentage of U.S. emissions comes from the top 10 states?- How does population relate to emissions per person?- Where are major emissions concentrations located geographically?
## Data Engineering Concepts Demonstrated- Medallion Architecture- Bronze, Silver, and Gold data modeling- Delta Lake tables- Unity Catalog- SQL-based ETL transformations- Data type standardization- Data quality validation- Aggregation and ranking- Window functions- Common Table Expressions- Analytical metric creation- Dashboard serving layer- Git and GitHub version control
## Current Pipeline Status
The project currently includes:- Raw CSV ingestion into a Bronze Delta table- Silver-layer cleaning and validation- Gold-layer business aggregations- Dashboard integration with Gold tables- Source-controlled SQL transformations- Source-controlled Databricks dashboard
## Future Improvements- Orchestrate Bronze → Silver → Gold using Databricks Workflows- Schedule automatic pipeline runs- Add pipeline failure handling and monitoring- Add incremental ingestion for newly arriving files- Add year-over-year emissions analysis- Add dashboard filters for state and county- Add additional environmental and demographic metrics- Add automated data-quality checks
