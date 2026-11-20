# DSA 405 Project: Wake County Restaurants and Income

**Tanvi Birru (tbirru) · DSA 405 Section 002 · Fall 2026**

## What this project is and what it found

This project asks whether the number of restaurants in a Wake County, North Carolina zip code is related to that zip code's median household income. It combines Wake County food facility inspection records with U.S. Census Bureau income estimates, joins them by zip code, and tests the relationship.

**Finding:** across the 36 Wake County zip codes with both restaurant and income data, there is no relationship between restaurant count and median income (Pearson r = 0.00, p = 0.99). Counting all food facility types gives the same result (r = 0.09, p = 0.61). Restaurant counts seem to follow population and commercial activity rather than income, but this project does not adjust for population or area, so that explanation is not tested.

## Data sources

| Source | Publisher | Access | License |
|---|---|---|---|
| [Restaurant / food facility inspections](https://maps.wake.gov/arcgis/rest/services/Inspections/RestaurantInspectionsOpenData/MapServer/0) | Wake County GIS Open Data | ArcGIS REST API, paged with `requests` | CC0 1.0 Universal |
| [ACS 2023 5 year estimates, median household income (`B19013_001E`) by ZCTA](https://api.census.gov/data/2023/acs/acs5) | U.S. Census Bureau | Census Data API with `requests` | Public domain (U.S. government data) |

The Wake County raw pull from October 2, 2026 is saved unmodified at `data/raw/wake_restaurants.csv` (4,182 rows, 15 columns). Source and pull date are recorded in `data/raw/SOURCES.md`.

## How to run it

1. Open `DSA405_002_FA26_P4_tbirru.ipynb` in Google Colab.
2. Optional: add a free Census API key as a Colab secret named `CENSUS_KEY`. The notebook also works without one (it makes a single keyless request).
3. Click **Runtime → Restart and run all.**

What happens:

* The notebook calls both APIs and caches every raw response in `data/raw/`. Later runs read from the cache and make no requests.
* If the Wake County API is down or times out, the notebook logs a warning and falls back to the saved raw pull at `data/raw/wake_restaurants.csv` in this repo. The output says which source was used.
* Cleaned tables are written to `data/processed/` and the figure to `figures/`.
* A full run takes about 3 to 4 minutes if the Wake County API is down (it waits for timeouts before falling back), and under a minute otherwise.

No API keys or passwords are stored in this repo.

## Repo structure

```
dsa405-project/
├── README.md                              this file
├── DSA405_002_FA26_P2_tbirru.ipynb        P2: data audit, cleaning log, provenance brief
├── DSA405_002_FA26_P3_tbirru.ipynb        P3: acquisition, join design, verification
├── DSA405_002_FA26_P4_tbirru.ipynb        P4: final notebook, raw data to final figure (run this one)
├── data/
│   └── raw/
│       ├── wake_restaurants.csv           Wake County raw pull, Oct 2, 2026 (never edited)
│       └── SOURCES.md                     source URL and pull date
└── assignments/
    └── labs/                              course labs
```

Created when the notebook runs (not committed):

```
data/raw/*.json              cached API responses
data/processed/              facilities_with_income.csv, zip_density_income.csv
figures/                     restaurants_vs_income.png
```
