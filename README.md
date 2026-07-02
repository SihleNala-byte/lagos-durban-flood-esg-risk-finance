# Urban Flood Risk & Climate Finance: A Comparative Analysis of Lagos, Nigeria and Durban, South Africa

A end-to-end analytical pipeline integrating climate science, spatial analysis, statistical modelling, and financial scenario planning to assess urban flood risk and inform insurance, ESG finance, and adaptation investment decisions in two major African coastal cities.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

---

## Overview

Lagos and Durban are both densely populated, low-lying African coastal cities facing escalating flood risk but for very different structural reasons. This project builds a reproducible, data-driven pipeline to diagnose *why* flooding is happening, whether it's getting worse, how far the damage reaches, and what mitigation investment is economically justified, framed explicitly for insurance pricing, parametric trigger design, ESG green bond eligibility, and TCFD/ISSB physical risk disclosure use cases.

## Research Questions

1. **Why** is flooding happening in both cities?
2. **Has** flooding increased over time?
3. **How far** does flood damage reach, spatially and economically?
4. **What** mitigation solutions could reduce future flood risk?

## Key Findings

- **The climate-flood paradox:** Both cities show *declining* annual rainfall totals alongside *increasing* flood frequency, explained by warming-driven storm intensification (Clausius-Clapeyron relation) rather than overall wetter conditions.
- **Two distinct risk profiles:** Lagos faces density-driven flood risk on flat, low-lying coastal terrain; Durban faces topography-amplified runoff, with steep hills and narrow valleys funnelling water toward a vulnerable coastal strip.
- **Structural vulnerability beyond climate:** OLS regression models show large gaps between predicted and observed damages (Lagos ~14×, Durban ~7× underestimates), pointing to structural urban vulnerability, not climate variables alone, as the primary driver of realised loss.
- **Investment case:** A cost-benefit "invest vs. do nothing" scenario analysis (2025-2050) returns central-case benefit-cost ratios of **3.5×** for Lagos and **4.2×** for Durban.

## Repository Structure

```
lagos-durban-flood-esg-risk-finance/
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_data_loading_and_cleaning.ipynb
│   ├── 02_climate_trend_analysis.ipynb
│   ├── 03_urbanisation_analysis.ipynb
│   ├── 04_emdat_disaster_analysis.ipynb
│   ├── 05_regression_modelling.ipynb
│   ├── 06_spatial_flood_risk_mapping.ipynb
│   └── 07_scenario_modelling_and_cba.ipynb
├── data/
│   ├── raw/          (gitignored — too large / licensing)
│   └── processed/    (small derived CSVs only)
├── figures/
│   ├── climate_trends.png
│   ├── flood_frequency_trend.png
│   ├── regression_diagnostics.png
│   ├── spatial_risk_map_lagos.png
│   ├── spatial_risk_map_durban.png
│   └── cba_scenario_comparison.png
└── report/
    └── Flood_Risk_Finance_Report.docx

```

## Methodology

### Phase 1 — Diagnosing the trend
| Step | Notebook | Method |
|---|---|---|
| 1 | `01_data_loading_and_cleaning.ipynb` | Data ingestion and cleaning across all sources |
| 2 | `02_climate_trend_analysis.ipynb` | ERA5 precipitation/temperature trend analysis |
| 3 | `03_urbanisation_analysis.ipynb` | World Bank + GHSL built-surface urbanisation analysis |
| 4 | `04_emdat_disaster_analysis.ipynb` | EM-DAT flood event analysis + Mann-Kendall trend testing (Sen's slope) |

### Phase 2 — Quantifying and pricing the risk
| Step | Notebook | Method |
|---|---|---|
| 5 | `05_regression_modelling.ipynb` | Log-linear OLS regression of flood severity drivers |
| 6 | `06_spatial_flood_risk_mapping.ipynb` | Composite spatial flood risk scoring (elevation, slope, built-surface) |
| 7 | `07_scenario_modelling_and_cba.ipynb` | 2025–2050 scenario modelling, DCF/NPV/BCR cost-benefit analysis |

## Data Sources

| Source | Used for |
|---|---|
| [ERA5 Reanalysis](https://cds.climate.copernicus.eu/) | Precipitation and temperature time series |
| [EM-DAT](https://www.emdat.be/) | Historical flood disaster records |
| [World Bank Open Data](https://data.worldbank.org/) | National/urban population statistics |
| [GHSL](https://ghsl.jrc.ec.europa.eu/) | Built-surface raster layers |
| [SRTM DEM](https://www2.jpl.nasa.gov/srtm/) | Digital elevation model for slope/terrain analysis |

*Raw data files are not stored in this repository due to size and licensing. See links above to download directly; processed/derived subsets used in the notebooks are included in `data/processed/` where file size permits.*

## Visualisations

| | |
|---|---|
| ![Climate trends](figures/climate_trends.png) | ![Flood frequency trend](figures/flood_frequency_trend.png) |
| ![Regression diagnostics](figures/regression_diagnostics.png) | ![CBA comparison](figures/cba_scenario_comparison.png) |
| ![Lagos spatial risk map](figures/spatial_risk_map_lagos.png) | ![Durban spatial risk map](figures/spatial_risk_map_durban.png) |

*(Add your exported PNGs to `figures/` with these filenames, or update the paths above to match.)*

## Installation

```bash
git clone https://github.com/<SihleNala-byte>/lagos-durban-flood-risk-finance.git
cd lagos-durban-flood-risk-finance
pip install -r requirements.txt
jupyter lab
```
h
Then open the notebooks in `notebooks/` in numbered order.

## Full Report

The complete write-up: including methodology detail, full regression tables, and city-specific investment packages — is available in [`report/Flood_Risk_Finance_Report.docx`](report/Flood_Risk_Finance_Report.docx).

## Limitations

- World Bank national-level statistics used as city-level proxies where city-specific data was unavailable.
- Post-merge sample sizes in the regression models are relatively small, limiting statistical power.
- Composite spatial risk scores are relative rankings, not absolute damage predictions.

## Frameworks Referenced

TCFD · ISSB · ESG · Climate Bonds Initiative · SSP2-4.5 · Parametric Insurance · Nature-Based Solutions (NbS)

## Author

**Sihle Nala** — [LinkedIn] · [Portfolio] · Drsihlenala@gmail.com

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
