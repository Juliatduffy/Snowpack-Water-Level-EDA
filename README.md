# Utah Snowpack EDA  
**Analyzing the Relationship Between Snowpack Variation, Precipitation, and Water Levels in the Great Salt Lake**

**Author:** Julia Duffy  
**Date:** April 30, 2025  
**Institution:** University of Utah  

**Notebook:** [FINAL_PROJECT.ipynb](FINAL_PROJECT.ipynb)  
**Colab link:** [FINAL_PROJECT_GOOGLE_COLAB](https://colab.research.google.com/drive/1fOIxD389hL0qJZhHIHht_OV5O52PTJ9W?usp=sharing)

---

## Table of Contents

1. [Abstract](#abstract)  
2. [Introduction](#introduction)  
3. [Central Question](#central-question)  
4. [Data Sources](#data-sources)  
5. [Data Retrieval & Cleaning](#data-retrieval--cleaning)  
6. [Visualizations](#visualizations)  
7. [Statistical Tests](#statistical-tests)  
8. [Limitations](#limitations)  
9. [Conclusion](#conclusion)  
10. [Sources](#sources)  

---

## Abstract

This project seeks to compare the impact of snow water equivalent (SWE) from the mountains and precipitation in Salt Lake County on Great Salt Lake levels from 01-01-2000 to 01-01-2025. Using lagged correlation, linear regression, normality tests, and Pearson correlation, we find that mountain snowfall has a weak but significant relationship to lake elevation—maximized at a 70-day delay—while same-day SWE and precipitation show no immediate effect.

## Introduction

Great Salt Lake levels have steadily declined over recent decades, exposing lakebed dust loaded with pesticides, arsenic, selenium, and other toxins. When winds pick up, these particles drift into nearby communities, posing a growing public-health risk. Understanding how snowmelt and rainfall influence lake elevation can inform better water management and dust-control strategies.

## Central Question

What drives Great Salt Lake elevation, and how long does it take mountain snowmelt to reach the lake?
1. Which variable has the stronger relationship to lake levels—mountain SWE or Salt Lake County precipitation?  
2. Is there a clear time lag between snowpack peaks and subsequent rises in the lake?

## Data Sources

All data span January 1, 2000 to January 1, 2025:
- **Brighton SNOTEL SWE** (USDA NRCS): Daily snow-water equivalent (inches) measuring water contained in the snowpack.  
- **Salt Lake County Precipitation** (USDA NRCS): Daily rainfall accumulation (inches) near the lake’s southern shore.  
- **Great Salt Lake Elevation** (USGS Hydro Mapper): Daily lake-level (ft) measurements.

## Data Retrieval & Cleaning

1. Download CSVs and parse `Date` as datetime.  
2. Rename columns, drop unused fields.  
3. Inner-join all three datasets on `Date`.  
4. Confirm zero missing values—no interpolation needed.

## Visualizations

1. **Full-Period Time Series:** Trends & seasonality—SWE peaks each spring; lake peaks mid-summer; both show multi-decade decline.  
2. **2024 Time Series:** Zoom on one year to illustrate lag effects.  
3. **Lag-Correlation Plot:** Pearson _r_ for 0–360-day delays (10-day steps); peak at 70 days.  
4. **No-Lag Scatter & Regression:** SWE vs. lake level same day; OLS fit shows near-flat slope.  
5. **70-Day Lag Scatter & Regression:** SWE shifted 70 days earlier vs. lake level; OLS fit shows steeper slope.  
6. **Precipitation vs. Lake Level:** Same-day scatter & regression; slight negative slope, no real correlation.

## Statistical Tests

- **Lagged Pearson Correlation:** _r_≈0.20 at 70 days (p≈0) → weak but significant.  
- **No-Lag Regression:** slope≈0.01 ft/in, _R²_≈0.001 → negligible.  
- **70-Day Lag Regression:** slope≈0.06 ft/in, _R²_≈0.04 → small improvement.  
- **Precipitation Regression:** slope≈–0.13 ft/in, _R²_≈0 → no predictive value.

## Limitations

- SWE from only one SNOTEL station and precipitation from one site—limited representativeness.  
- Excludes evaporation, groundwater, diversions, and climate-change factors.  
- Assumes historical stationarity in water management and climate practices.

## Conclusion

Mountain SWE has a modest delayed effect (~70 days) on Great Salt Lake levels. Immediate snowpack and local rainfall offer virtually no predictive power. Despite limitations, these findings highlight the nuanced timing of snowmelt contributions to lake elevation.

## Sources

- https://wcc.sc.egov.usda.gov/nwcc/sensors  
- https://www.sltrib.com/news/environment/2019/02/16/utah-snowpack-packed-with/  
- https://www.nrcs.usda.gov/utah/snow-survey  
- https://water.utah.gov/reservoirlevels/  
- https://webapps.usgs.gov/gsl/data.html  
