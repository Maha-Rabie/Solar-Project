# ☀️ Solar Power Generation — Data Analysis Project

A Python data analysis project that explores the relationship between atmospheric and meteorological conditions and the power output of a solar panel installation. The dataset contains 4,213 hourly observations across 21 features, with `generated_power_kw` as the target variable.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Repository Structure](#repository-structure)
- [Dataset](#dataset)
  - [Feature Descriptions](#feature-descriptions)
  - [Dataset Summary](#dataset-summary)
- [Notebook Walkthrough](#notebook-walkthrough)
- [Requirements](#requirements)
- [Running the Notebook](#running-the-notebook)

---

## Project Overview

Understanding what drives solar power output is essential for grid planning, energy forecasting, and site evaluation. This project loads a real-world hourly solar generation dataset, inspects its structure, and lays the foundation for exploratory data analysis (EDA) and predictive modelling.

The notebook covers:

- Loading and previewing the dataset
- Inspecting shape, column names, data types, and null counts
- Understanding the feature space — weather, cloud cover, solar geometry, and wind conditions

---

## Repository Structure

```
Solar-Project/
├── Untitled.ipynb   ← Jupyter notebook with data loading and initial exploration
└── spg.csv          ← Solar power generation dataset (4,213 rows × 21 columns)
```

---

## Dataset

**File:** `spg.csv`  
**Rows:** 4,213 hourly observations  
**Columns:** 21 (20 input features + 1 target)  
**No missing values** across any column

### Feature Descriptions

| Column | Type | Description |
|---|---|---|
| `temperature_2_m_above_gnd` | float64 | Air temperature 2 metres above ground (°C) |
| `relative_humidity_2_m_above_gnd` | int64 | Relative humidity 2 m above ground (%) |
| `mean_sea_level_pressure_MSL` | float64 | Mean sea level pressure (hPa) |
| `total_precipitation_sfc` | float64 | Total precipitation at surface (mm) |
| `snowfall_amount_sfc` | float64 | Snowfall amount at surface (mm) |
| `total_cloud_cover_sfc` | float64 | Total cloud cover at surface (%) |
| `high_cloud_cover_high_cld_lay` | int64 | High-altitude cloud cover (%) |
| `medium_cloud_cover_mid_cld_lay` | int64 | Mid-altitude cloud cover (%) |
| `low_cloud_cover_low_cld_lay` | int64 | Low-altitude cloud cover (%) |
| `shortwave_radiation_backwards_sfc` | float64 | Shortwave (solar) radiation at surface (W/m²) |
| `wind_speed_10_m_above_gnd` | float64 | Wind speed 10 m above ground (m/s) |
| `wind_direction_10_m_above_gnd` | float64 | Wind direction 10 m above ground (degrees) |
| `wind_speed_80_m_above_gnd` | float64 | Wind speed 80 m above ground (m/s) |
| `wind_direction_80_m_above_gnd` | float64 | Wind direction 80 m above ground (degrees) |
| `wind_speed_900_mb` | float64 | Wind speed at 900 mb pressure level (m/s) |
| `wind_direction_900_mb` | float64 | Wind direction at 900 mb pressure level (degrees) |
| `wind_gust_10_m_above_gnd` | float64 | Wind gust speed 10 m above ground (m/s) |
| `angle_of_incidence` | float64 | Angle of solar incidence on the panel (degrees) |
| `zenith` | float64 | Solar zenith angle — sun's angle from vertical (degrees) |
| `azimuth` | float64 | Solar azimuth angle — sun's compass bearing (degrees) |
| `generated_power_kw` | float64 | **Target — solar power generated (kW)** |

### Dataset Summary

- **Shape:** 4,213 rows × 21 columns
- **No null values** in any column
- **Data types:** 17 float64, 4 int64
- **Power range (from data preview):** ~20 kW (heavily overcast) to ~2,640 kW (clear sky, optimal angle)

The first few rows show clear-sky conditions with zero cloud cover and rising power as the zenith angle decreases through the morning. The last few rows show fully overcast conditions (100% cloud cover across all layers) with correspondingly low power output, demonstrating the strong influence of cloud cover on generation.

---

## Notebook Walkthrough

The notebook (`Untitled.ipynb`) steps through the following:

**1. Import libraries**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

**2. Load the dataset**

```python
df = pd.read_csv('spg.csv')
```

**3. Preview the data**

```python
df.head()   # first 5 rows
df.tail()   # last 5 rows
```

The `head()` output shows clear-sky morning hours with power rising from 454 kW to 2,640 kW as the sun climbs. The `tail()` shows overcast afternoons where power drops to as low as 20 kW despite similar solar geometry angles, highlighting the dominant effect of cloud cover.

**4. Inspect structure**

```python
df.info()    # shape, dtypes, non-null counts
df.columns   # full list of feature names
df.shape     # (4213, 21)
df.dtypes    # per-column types
```

The `df.info()` output confirms 4,213 complete records with no missing values — the dataset is clean and ready for EDA or modelling without imputation.

---

## Requirements

- Python 3.7+
- Jupyter Notebook or JupyterLab

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

---

## Running the Notebook

```bash
# Clone the repository
git clone https://github.com/Maha-Rabie/Solar-Project.git
cd Solar-Project

# Launch Jupyter
jupyter notebook Untitled.ipynb
```

Make sure `spg.csv` is in the same directory as the notebook — it is loaded with a relative path (`pd.read_csv('spg.csv')`).

---

## Possible Next Steps

- **Exploratory Data Analysis** — correlation heatmap, distribution plots, power vs. radiation scatter plots
- **Feature engineering** — time-of-day extraction if timestamps are available, cloud cover composite score
- **Predictive modelling** — regression models (Linear Regression, Random Forest, XGBoost) to predict `generated_power_kw` from weather inputs
- **Feature importance** — identify which variables (radiation, zenith, cloud cover) most strongly drive power output

---

## License

This project is part of the **Maha-Rabie** repository. See the root repository for license details.
