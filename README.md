# Burning Value: Wildfire Risk and Housing Markets

A data analysis project exploring how wildfire risk relates to housing markets, income, and real estate investment potential in Los Angeles County — built as part of a mid-term project on wildfire exposure and property values.

## What this notebook does

`LAFiresFinalProject.ipynb` merges wildfire hazard data with housing and demographic data at the ZIP-code level for LA County, then walks through three hypotheses and a series of increasingly polished visualizations:

1. **Hypothesis 1** — Do higher-income ZIP codes have lower wildfire exposure? (Tested with correlation, a scatterplot, an income-quartile boxplot, and a colored scatterplot incorporating home value.)
2. **Hypothesis 3** — Does a catastrophic wildfire (the 2018 Camp Fire, Butte County) permanently depress local home values relative to the state average? (Tested with absolute and indexed home-value recovery charts, and a 1/3/5-year relative-performance comparison.)
3. A series of map-based visualizations of the same core finding — that some high-value LA County ZIP codes carry substantial wildfire exposure — building from a basic interactive choropleth up through:
   - A bivariate hex-mosaic map (color = wildfire exposure, size = home value), styled after climate-reporting graphics like drought-intensity maps
   - An editorial "bubble map" of historical major wildfires (size = acres burned), both as a static image and an interactive version, styled after data-journalism graphics like the LA Times' "Pinpointing Pollution"
   - **The LA Wildfire Risk & Investment Explorer** — an interactive dashboard with toggleable layers (wildfire risk, income, home value, appreciation, an Investment Opportunity Score, and an Investment Category classification), historical fire locations, and numbered "Top Investment Picks" pins
   - **A professional dashboard variant** — the same data restyled with smooth ZIP-boundary choropleths and a muted, corporate-friendly color palette, closer to what a real estate firm's internal tool might look like

### The Investment Opportunity Score

Each ZIP is scored as its **percentile rank on 10-year home price appreciation minus its percentile rank on wildfire exposure**, weighted equally. This keeps either factor from dominating just because it happens to have a wider raw numeric range (an earlier version divided appreciation by a wildfire-exposure term that barely moved the needle, and was replaced after review). The score is an illustrative screening metric for further due diligence — not a real underwriting formula, and not investment advice.

## Data sources

| Source | How it's loaded |
|---|---|
| [Zillow Home Value Index (ZHVI)](https://www.zillow.com/research/data/), ZIP-level | Downloaded directly from Zillow's public research CSV URL |
| U.S. Census ACS median household income by ZCTA | `HouseholdIncome.csv` (included in this repo) |
| [CAL FIRE Fire Hazard Severity Zones](https://www.fire.ca.gov/what-we-do/fire-resource-assessment-program/fire-hazard-severity-zones) | `FHSZSRA_23_3.gdb` (Esri File Geodatabase, included in this repo) |
| [CAL FIRE FRAP historical fire perimeters](https://data.ca.gov/dataset/california-fire-perimeters-all) | Auto-downloaded and cached locally on first run (~250MB) |
| U.S. Census TIGER/Line ZCTA boundaries | Downloaded directly from a Census Bureau public URL |

## Running it

### In Google Colab
1. Upload `LAFiresFinalProject.ipynb` to Colab (File → Upload notebook).
2. Upload `HouseholdIncome.csv` and the `FHSZSRA_23_3.gdb` folder into the Colab session's files (drag-and-drop into the file browser pane works for the folder in Chrome), or mount Google Drive if you'd rather they persist across sessions.
3. Run all cells — the first cell installs `geopandas`, `folium`, and `contextily`, which Colab doesn't include by default.

### Locally (Jupyter / VS Code)
```bash
pip install pandas geopandas altair folium matplotlib contextily
```
Then open the notebook and run all cells from the top. `HouseholdIncome.csv` and `FHSZSRA_23_3.gdb` are read via relative paths, so keep them in the same folder as the notebook.

Running the notebook regenerates the interactive maps (`.html`) and static charts (`.png`) as local output files — these aren't tracked in this repo, since they're fully reproducible from the notebook and its two input files.

## Repo contents
- `LAFiresFinalProject.ipynb` — the full analysis notebook
- `HouseholdIncome.csv` — Census median household income by ZCTA
- `FHSZSRA_23_3.gdb/` — CAL FIRE Fire Hazard Severity Zone polygons (State Responsibility Area)
