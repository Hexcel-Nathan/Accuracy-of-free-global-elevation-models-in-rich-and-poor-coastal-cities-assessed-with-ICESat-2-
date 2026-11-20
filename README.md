# Free global elevation models in rich and poor coastal cities

Code for the study *"Who can check their flood maps? Accuracy of free global elevation models in rich and poor coastal cities, assessed with ICESat-2"* (Samson, in preparation).

**Author:** Jonathan Ayomide Samson, School of Geographical and Earth Sciences, University of Glasgow ([ORCID 0009-0009-0566-5371](https://orcid.org/0009-0009-0566-5371))

## What the study does

Coastal cities without airborne LiDAR, most of them in lower-income countries, depend on free global digital elevation models (DEMs) for flood mapping. This study tests whether those DEMs are less accurate in such cities.

- **DEMs tested:** Copernicus DEM GLO-30 (2024_1 release), FABDEM, DeltaDTM v1.1
- **Reference:** ICESat-2 ATL08 ground heights (2019–2023), used in every city
- **Test of the reference:** airborne LiDAR in the high-income cities (USGS 3DEP 1 m; Environment Agency LiDAR Composite DTM 2022)
- **Cities (paired by landscape):**

| Lower-middle income | High income |
| --- | --- |
| Lagos | Miami |
| Mumbai | New York |
| Karachi | Los Angeles |
| Abidjan | Houston |
| Dar es Salaam | London |

Analysis is limited to urban land below 10 m (selected by ICESat-2 height). Errors are summarised with bias, RMSE, NMAD and LE90, compared with linear mixed-effects models (random intercept for city), tested for the effect of building height and density (GHSL), and translated into urban area below 1, 2 and 3 m.

## Repository contents

| File | What it is |
| --- | --- |
| `T17_DEM_accuracy_coastal_cities.ipynb` | The full analysis, from data download to figures |
| `requirements.txt` | Python packages used |
| `results/` | Output tables (`table_*.csv`) [add from Google Drive] |
| `figures/` | Figures 1–3 (`fig*.png`) [add from Google Drive] |

Larger intermediate files (ICESat-2 point files, sampled points) are archived at [Zenodo DOI].

## How to run

1. Create a free [NASA Earthdata](https://urs.earthdata.nasa.gov) account.
2. Register a Google Cloud project for [Google Earth Engine](https://code.earthengine.google.com/register) (noncommercial use).
3. Open the notebook in Google Colab and replace `YOUR-PROJECT-ID` in section 1.2 with your project ID.
4. Run the cells from top to bottom. Outputs are saved to `MyDrive/T17` in Google Drive. If Colab disconnects, run the notebook again: completed steps reload from Drive instead of repeating.

The ICESat-2 download takes about one to two hours for all ten cities; Earth Engine sampling takes a similar time.

## Main outputs

| Output | Content |
| --- | --- |
| `table_filter_counts.csv` | Points remaining after each filter, per city |
| `table_icesat2_vs_lidar.csv` | ICESat-2 against LiDAR, with datum offsets |
| `table_icesat2_vs_lidar_dem_check.csv` | DEM errors measured against ICESat-2 and against LiDAR |
| `table_errors_by_city.csv` | DEM error statistics by city |
| `table_errors_by_landcover_rich_poor.csv` | DEM error statistics by land cover and income group |
| `table_model_poor_vs_rich.csv`, `table_model_poor_vs_rich_builtup.csv` | Mixed-effects model results |
| `table_model_building_form.csv` | Models with and without building height and density |
| `table_flood_area.csv` | Urban area below 1, 2 and 3 m by DEM |

## Data sources

- Copernicus DEM GLO-30, 2024_1 release (ESA / Airbus), via Google Earth Engine
- FABDEM (Hawker et al., 2022), via the GEE Community Catalog. Licence: CC BY-NC-SA 4.0
- DeltaDTM v1.1 (Pronk et al., 2024), via the GEE Community Catalog
- ICESat-2 ATL08 (Neuenschwander and Pitts, 2019), NASA NSIDC DAAC
- USGS 3DEP 1 m DEM; Environment Agency LiDAR Composite DTM 2022
- ESA WorldCover 10 m v200; GHSL GHS-SMOD, GHS-BUILT-H and GHS-BUILT-S (R2023A)

## Use of AI tools

An AI assistant (Claude, Anthropic) helped write and the debug the code while the author checked all code and outputs. 

## Licence

Code: MIT. Input datasets keep their own licences.

## Citation

[Paper or preprint reference and the Zenodo DOI TO BE ADDED once available.]
