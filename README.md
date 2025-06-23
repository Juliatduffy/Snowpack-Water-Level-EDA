# Utah Snowpack EDA  
**Analyzing the Relationship Between Snowpack Variation, Precipitation, and Water Levels in the Great Salt Lake**

**Author:** Julia Duffy  
**Date:** April 30, 2025  
**Institution:** University of Utah  

**Notebook:** [FINAL_PROJECT.ipynb](FINAL_PROJECT.ipynb)  
**Colab link:** [https://colab.research.google.com/drive/1fOIxD389hL0qJZhHIHht_OV5O52PTJ9W](https://colab.research.google.com/drive/1fOIxD389hL0qJZhHIHht_OV5O52PTJ9W?usp=sharing)

---

## Table of Contents

1. [Abstract](#abstract)  
2. [Questions](#questions)  
3. [Data Sources & Cleaning](#data-sources--cleaning)  
4. [Methods & Visualizations](#methods--visualizations)  
5. [Statistical Tests](#statistical-tests)  
6. [Results & Findings](#results--findings)  
7. [Limitations](#limitations)  
8. [Conclusion](#conclusion)  
9. [Project Structure](#project-structure)  
10. [Dependencies & Usage](#dependencies--usage)  
11. [License](#license)  

---
---

## Abstract  
This project seeks to compare the impact of various factors on water levels in the Great Salt Lake. In this analysis, daily snow water equivalent (SWE) measurements from the mountains and daily precipitation records from Salt Lake County are paired with lake-level data from 01-01-2000 through 01-01-2025 to identify which variable has the strongest effect on lake elevation in the Great Salt Lake. This EDA uses several different analysis techniques, such as a lagged correlation analysis, linear regression analysis, normality test, and Pearson correlation test. It was found that snowfall in the mountains has a very weak but significant relationship to water levels in the Great Salt Lake. Introducing a time delay of 70 days maximized the correlation between SWE levels and water levels in the lake. Precipitation and SWE seemed to have no immediate impact on water levels in the lake. :contentReference[oaicite:1]{index=1}

## Introduction  
It is no secret that water levels in the Great Salt Lake have been steadily declining over the past few decades. As the shoreline retreats, more and more of the lakebed has been exposed, leaving fine dust, minerals, and salt on the surface. When the winds kick up, that fine dust is kicked into the air, and tiny particles drift into nearby towns. This has posed a serious health threat to the general public, and the situation is only worsening. Because the lake collects runoff from across Utah, those dust clouds often carry pesticides, arsenic, selenium, and other toxins as well. :contentReference[oaicite:2]{index=2}

## Central Question  
The goal of this analysis is to better understand what factors affect water levels in the Great Salt Lake and how long it takes for snowmelt in the mountains to replenish the lake. This analysis asks two central questions:
1. Which variable has the stronger relationship to Great Salt Lake elevation—mountain snowpack (SWE) or Salt Lake County precipitation?  
2. Is there a clear time lag between increases in snowpack and subsequent rises in the Great Salt Lake? :contentReference[oaicite:3]{index=3}

## Data Sources  
Data for this analysis was sourced from the U.S. Department of Agriculture NRCS SNOTEL Data as well as the Great Salt Lake Hydro Mapper (USGS). All three datasets span January 1, 2000 to January 1, 2025. The three datasets used were:  
- **Brighton SNOTEL SWE:** Daily snow‐water equivalent (inches) from USDA NRCS mountain stations; measures the water contained in snowpack.  
- **Salt Lake County Precipitation:** Daily rainfall accumulation (inches) from a SNOTEL station near the lake’s southern shore.  
- **Great Salt Lake Elevation:** Daily water level (ft) from USGS Hydro Mapper. :contentReference[oaicite:4]{index=4}

## Data Retrieval and Cleaning  
All three CSVs were downloaded and uploaded to GitHub. No missing values required interpolation. Cleaning steps:  
1. Parse `Date` as datetime.  
2. Rename columns for clarity; drop unnecessary fields.  
3. Inner-join on `Date`.  
After merging, no missing values remained, and no imputation was necessary. :contentReference[oaicite:5]{index=5}

## Visualizations

### Visualization 1: Full-Period Time Series Line Graph  
Shows long-term trends and seasonality: SWE peaks each spring, lake level peaks mid-summer, and a clear 25-year decline in lake elevation; SWE declines appear steeper than lake levels. :contentReference[oaicite:6]{index=6}

### Visualization 2: 2024 Time Series Line Graph  
Zooms into a single year to illustrate how introducing time delays changes the SWE–lake relationship, guiding identification of the optimal lag. :contentReference[oaicite:7]{index=7}

### Visualization 3: Lag-Correlation Graph  
Plots Pearson _r_ for delays from 0–360 days (10-day steps); the highest correlation occurs at a 70-day lag. :contentReference[oaicite:8]{index=8}

### Visualization 4: No-Lag Scatter Plot and Regression Line  
SWE vs. lake elevation for the same date, with an OLS fit. Wide variance and near-flat slope indicate a negligible same-day correlation. :contentReference[oaicite:9]{index=9}

### Visualization 5: 70-Day Lag Scatter Plot and Regression Line  
SWE shifted 70 days earlier vs. lake elevation today, with OLS fit. Tighter clustering and steeper slope confirm the modest improvement in correlation. :contentReference[oaicite:10]{index=10}

### Visualization 6: Precipitation vs. Lake Level Scatter Plot and Regression Line  
Daily precipitation vs. lake elevation, with OLS fit showing a slight negative slope and effectively zero explanatory power. :contentReference[oaicite:11]{index=11}

## Statistical Tests

### Correlation Testing to Determine Time Delay  
A series of Pearson correlation tests (lag 0–360 days) found the maximum _r_≈0.199 at 70 days (p≈0), indicating a weak but statistically significant delayed effect. :contentReference[oaicite:12]{index=12}

### Regression Modeling To Determine Relationships Between Variables  
- **No Lag:** Slope ≈ 0.01 ft/in, intercept 4,195.12 ft, _R²_≈0.001—no meaningful same-day predictive power.  
- **70-Day Lag:** Slope ≈ 0.06 ft/in, intercept 4,194.72 ft, _R²_≈0.04—small improvement, still weak.  
- **Precipitation:** Slope ≈ –0.13 ft/in, intercept 4,195.20 ft, _R²_≈0—no predictive value. :contentReference[oaicite:13]{index=13}

## Limitations  
- SWE from only one SNOTEL (Brighton) and precipitation from one station—limited geographic scope.  
- Excludes evaporation, groundwater use, diversions, and climate-change factors.  
- Assumes historical stationarity in water management and climate practices.  
- Great Salt Lake’s urban context and multifaceted use may disrupt natural hydrologic inputs. :contentReference[oaicite:14]{index=14}

## Conclusion  
Mountain SWE exhibits a modest but statistically significant influence on Great Salt Lake levels after a ~70-day delay. Immediate SWE and local precipitation show virtually no relationship. Despite limitations, these findings highlight the delayed hydrologic link between snowpack and lake elevation. :contentReference[oaicite:15]{index=15}

## Sources  
- https://wcc.sc.egov.usda.gov/nwcc/sensors  
- https://www.sltrib.com/news/environment/2019/02/16/utah-snowpack-packed-with/  
- https://www.nrcs.usda.gov/utah/snow-survey  
- https://water.utah.gov/reservoirlevels/  
- https://webapps.usgs.gov/gsl/data.html  
