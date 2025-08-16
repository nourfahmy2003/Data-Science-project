# Satellite Launches & Population Analytics

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter)
![Plotly](https://img.shields.io/badge/Plotly-239120?logo=plotly&logoColor=white)

A data-driven exploration of global satellite activity, with optional per-capita views using population data. Two Jupyter notebooks transform the raw SATCAT catalogue into presentation-ready figures.

## Table of Contents
- [Repository Overview](#repository-overview)
- [Goals & Motivation](#goals--motivation)
- [Tech Stack](#tech-stack)
- [Data Sources](#data-sources)
- [How to Run](#how-to-run)
- [Notebook Highlights](#notebook-highlights)
- [Example Insights](#example-insights)
- [Suggested Repo Structure](#suggested-repo-structure)
- [Future Work](#future-work)
- [Exporting Figures](#exporting-figures)
- [Licensing & Attribution](#licensing--attribution)

## Repository Overview
- **finalproject.ipynb** – comprehensive analysis: ingest and clean the SATCAT file, engineer features, and build rich visuals (time series, leaderboards, orbit breakdowns, waffle charts, circle packing, optional maps).
- **ProjectFinale.ipynb** – streamlined "report" notebook producing a curated set of final figures.
- **world_population_2023.csv** – population reference (`Country`, `Population`) for per-capita metrics.
- **satcat.tsv** *(add separately)* – Satellite Catalog in TSV format used by both notebooks.

## Goals & Motivation
- Trace launch activity over time.
- Identify leading countries and organizations.
- Explore orbit and payload distributions.
- Enable population-adjusted comparisons.

## Tech Stack
Core: `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`  
Specialty visuals: `pywaffle`, `circlify`  
Optional mapping: `geopandas`, `pycountry`, `pycountry-convert`

### Quick start
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn plotly pywaffle circlify ipywidgets pillow pycountry pycountry-convert geopandas
```
If installing `geopandas` is problematic, comment out or skip mapping cells.

## Data Sources
- **satcat.tsv** – tab-separated satellite metadata (launch date, country/organization, orbit, status, etc.).
- **world_population_2023.csv** – country population reference for per-capita metrics.

Ensure country names align between datasets; adjust the mapping cells in the notebooks if needed.

## How to Run
1. Clone this repository and create a virtual environment.
2. Install dependencies (see above or `pip install -r requirements.txt`).
3. Place `satcat.tsv` in the project root.
4. Launch Jupyter and open a notebook:
   ```bash
   jupyter notebook
   ```
5. Run cells top-to-bottom, installing any missing libraries when prompted.

## Notebook Highlights
### `finalproject.ipynb`
- Load and clean `satcat.tsv` (parse dates, normalize categories).
- Engineer features such as launch year and groupings by country, orbit, and payload.
- Build exploratory visuals (annual trends, leaderboards, orbit composition, waffle charts, circle packing, optional geo maps).
- Optionally merge with `world_population_2023.csv` to compute satellites per capita.

### `ProjectFinale.ipynb`
- Rerun the essential pipeline.
- Output a curated set of figures suitable for reports or exporting.

## Example Insights
- Rapid growth in satellite deployments, especially in recent years.
- Activity concentrated among a handful of countries and operators.
- LEO dominates modern orbit choices.
- Per-capita views can reveal different leaders than absolute counts.

## Suggested Repo Structure
```
.
├─ finalproject.ipynb
├─ ProjectFinale.ipynb
├─ world_population_2023.csv
├─ satcat.tsv            # add this file
├─ figures/              # optional output directory
└─ README.md
```

## Future Work
- Build an interactive dashboard (e.g., Dash) for dynamic filtering.
- Classify payload purpose (communications, Earth observation, navigation, science).
- Integrate launch vehicle/provider data for deeper analysis.
- Automate refreshes of the Satellite Catalog.

## Exporting Figures
- **Matplotlib:** `plt.savefig("figures/plot.png", dpi=300, bbox_inches="tight")`
- **Plotly:** `fig.write_image("figures/plot.png", scale=2)` (requires `kaleido`).

## Licensing & Attribution
- Satellite data: attribute to the SATCAT source.
- Population data: include the original provider.
- Licensed under the [MIT License](LICENSE).
