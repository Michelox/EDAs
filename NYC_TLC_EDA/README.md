# Advanced EDA of NYC Yellow Taxi Trips

## Overview

This project presents a professional exploratory data analysis of New York City Yellow Taxi trip records. It is designed as a portfolio-grade data analysis notebook that can be executed in Google Colab without manually uploading datasets.

The analysis uses official NYC Taxi & Limousine Commission public data and focuses on demand, pricing, tipping behavior, operational speed, spatial flows, anomaly detection, and pickup zone segmentation.

## Dataset

The notebook uses the following public sources:

- NYC TLC Yellow Taxi monthly trip records in Parquet format
- NYC TLC taxi zone lookup table
- NYC TLC taxi zone spatial boundaries

Default analysis window:

- January 2024
- February 2024
- March 2024

The notebook can be scaled to additional months by editing the `YEAR_MONTHS` configuration variable.

## Main analysis components

The notebook includes:

1. **Automated data ingestion**
   - Downloads monthly Yellow Taxi Parquet files.
   - Downloads taxi zone lookup data.
   - Downloads official TLC taxi zone boundaries.

2. **Data quality audit**
   - Measures invalid timestamps.
   - Detects implausible durations, distances, speeds, amounts, passenger counts, and location IDs.
   - Reports retention from raw records to the clean analytical layer.

3. **Core EDA**
   - Trip volume
   - Gross booking value
   - Fare and tip distributions
   - Trip distance and duration distributions
   - Average speed and rush-hour behavior

4. **Temporal analysis**
   - Daily trip trends
   - Hour-of-day patterns
   - Day-of-week heatmaps
   - Rush-hour vs non-rush-hour comparisons

5. **Economic analysis**
   - Payment type behavior
   - Recorded tip patterns
   - Airport vs non-airport trip economics
   - Fare distribution analysis

6. **Spatial analysis**
   - Borough-level pickup distribution
   - Borough-to-borough origin-destination matrix
   - Top pickup zones
   - Zone-level pickup/drop-off imbalance
   - Choropleth maps using official TLC taxi zone geometries

7. **Corridor analysis**
   - Top origin-destination zone pairs
   - Route concentration across the highest-volume corridors

8. **Anomaly detection**
   - Uses an Isolation Forest model on trip-level operational and economic features.
   - Surfaces unusual combinations of duration, distance, speed, total amount, and tip percentage.
   - Produces a ranked anomaly inspection table.

9. **Zone segmentation**
   - Clusters pickup zones using operational metrics.
   - Uses PCA visualization for cluster interpretation.
   - Maps cluster assignments across taxi zones.

10. **Executive readout**
    - Generates a concise data-driven summary with computed metrics and recommended next steps.

## Technical stack

- Python
- DuckDB
- pandas
- NumPy
- Plotly
- GeoPandas
- scikit-learn
- SciPy
- Requests

DuckDB is used to query Parquet files efficiently without loading the full dataset into pandas memory. pandas is used for sampled visualizations and smaller aggregated tables.

## How to run

1. Open Google Colab.
2. Upload `NYC_Yellow_Taxi_Advanced_EDA_Colab.ipynb`.
3. Run the notebook from top to bottom.
4. Keep the default `YEAR_MONTHS` setting for a manageable first run.
5. Add more months only after confirming that the Colab runtime has sufficient memory and disk space.

## Configuration

The main configuration variables are:

```python
YEAR_MONTHS = ["2024-01", "2024-02", "2024-03"]
SAMPLE_ROWS = 250_000
RUN_GEOSPATIAL_MAPS = True
