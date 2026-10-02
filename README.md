# dsa405-project
This is my first line in my README.

# DSA 405 Project: Wake County Food Businesses and Income

## What this project is
This project asks whether the number of grocery stores and restaurants in an area is related to income level across Wake County, North Carolina zip codes. It combines two data sources: Wake County food facility records and U.S. Census Bureau income data by zip code. This milestone (P2) audits and cleans the Wake County food facility data and documents every cleaning decision.

## Where the data came from
- **Wake County food facilities:** pulled on October 2, 2026 from the Wake County government open data ArcGIS REST service (maps.wakegov.com). Licensed CC0 1.0 Universal. The raw pull is saved unmodified at `data/raw/wake_restaurants.csv` (4,182 rows, 15 columns). The exact source and date are recorded in `data/raw/SOURCES.md`.
- **Census Bureau income data:** American Community Survey 5-year estimates by zip code. This source is used in P3 and is not part of this milestone.

## How to run it
1. Open the notebook `DSA405_002_FA26_P2_[tbirru].ipynb` in Google Colab (use the "Open in Colab" button at the top of the notebook on GitHub).
2. Click **Runtime**, then **Restart and run all**.
3. The notebook reads the raw data directly from this repository over the web, so there is nothing to download first.

## Notes
- The code never writes to `data/raw/`. Cleaning is done on a copy in memory.
- The notebook contains the audit, data dictionary, cleaning log, row and column accounting, and provenance brief.
