# 🌃 Night Light Intensity and Conflict Correlation in Ukraine

This repository presents a data-driven exploration of the relationship between **night-time light intensities** and **conflict activity** in Ukraine, using geospatial and time series analysis in **R**.

---

## 🧠 Project Summary

Using data from satellite-derived night light imagery and conflict event datasets, this study investigates how **violent conflicts affect night-time luminosity** in key Ukrainian regions.

We aim to answer:
> 🕵️ *Is there a measurable relationship between light intensity and the intensity of conflict in different Ukrainian regions?*

---

## 📦 Tools & Libraries

This project was conducted using **R 4.4.3** with the following libraries:

- `tidyverse` 📊 — for data wrangling and visualization
- `raster`, `sf`, `sp` 🗺️ — for spatial data handling
- `ggplot2` 🎨 — for plotting
- `readr` — for efficient CSV parsing

⚠️ Some packages (like `raster`) mask base functions such as `select()` from `dplyr`.

---

## 📂 Data Sources

- **Night Light Data**: Satellite imagery capturing night-time light intensity across Ukrainian provinces (admin1 level).
- **Conflict Event Data**: ACLED-style conflict data including event type, actors, fatalities, coordinates, etc.
  - `~55,000` rows
  - 31 variables: location, actors, event date, fatalities, etc.

---

## 📈 Key Steps

1. **Data Loading**:
   - Used `readr::read_csv()` to import large-scale conflict event data.
   - Loaded raster-based night light data using `raster` and `sf`.

2. **Cleaning & Preprocessing**:
   - Grouped by `admin1` regions (e.g., Donetsk, Luhansk).
   - Summarized event frequencies and light intensity averages.
   - Dealt with missing coordinates, projection issues, and column type mismatches.

3. **Correlation Analysis**:
   - Calculated Pearson correlations between light intensity and conflict frequency per region.
   - Notable findings:
     - Donetsk: **-0.32**
     - Zaporizhia: **-0.29**
     - Luhansk: **-0.12**
     - Kharkiv: **-0.04**

4. **Visualization**:
   - Used `geom_smooth()` and `ggplot2` to plot trends.
   - Regression lines highlighted intensity drops in conflict zones.

---

## 🔍 Sample Output

```r
# Summary table of correlations
# A tibble: 4 x 2
admin1      | cor
------------|-----------------
Donetsk     | -0.323
Zaporizhia  | -0.297
Luhansk     | -0.120
Kharkiv     | -0.042
