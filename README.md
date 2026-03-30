# 🏥 UK Mortality Data Analytics Dashboard

An interactive Python dashboard analysing **5.2 million deaths** registered in England and Wales (2015–2024), built using Pandas, NumPy, Matplotlib, Seaborn, and Tkinter.

---

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Features](#features)
- [Charts & Visualisations](#charts--visualisations)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)
- [References](#references)

---

## About the Project

This project analyses mortality data published by the **Office for National Statistics (ONS)** to uncover geographic, demographic, and temporal patterns in deaths across England and Wales. The analysis spans 10 years of data (2015–2024) and explores trends across 42 Integrated Care Board (ICB) regions.

The project culminates in a **Tkinter GUI Dashboard** that lets users interactively explore the visualisations through a sidebar navigation menu.

---

## Dataset

| Property | Details |
|---|---|
| **Source** | [ONS – Deaths Registered in England and Wales](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/deaths/datasets/deathsregisteredsummarystatisticsenglandandwales) |
| **Published by** | Population Health Monitoring Group, ONS |
| **Published on** | 09 October 2025 |
| **Time Period** | 2015 – 2024 |
| **Total Rows** | 18,300 |
| **Columns** | 8 |

**Columns:** `Year`, `Area code`, `Area of usual residence`, `Geography Type`, `Sex`, `Place of death`, `Number of deaths`, `Percentage of deaths`

---

## Project Structure

```
📦 mortality-dashboard/
├── 📓 notebook.ipynb               # Main Jupyter Notebook (all sections)
├── 📊 annualdeaths2024.xlsx        # Raw ONS dataset
├── 🖼️ Chart1_top_5_ICB_death_rate.png
├── 🖼️ Chart2_top_5_places_of_death.png
├── 🖼️ Chart3_gender_comparison_by_death.png
├── 🖼️ Chart4_mortality_trend_2015-2024.png
├── 🖼️ Chart5_death_by_place_and_year_heatmap.png
└── 📄 README.md
```

---

## Features

### 🔧 Section 1 – Control Structures
- Loaded dataset directly from GitHub using `pd.read_excel()` with `openpyxl`
- Filtered 18,300 rows down to **7,560 relevant rows** using a `for` loop with `iterrows()`
- Filtering criteria: ICB geography only, Male/Female (excluding "All people"), specific places of death (excluding "All places")

### 🧩 Section 2 – Functions & Modules
Four reusable functions were built:

| Function | Purpose |
|---|---|
| `get_top_n()` | Returns top N values of any column by death count |
| `clean_data()` | Removes null values and duplicates |
| `calculate_gender_deaths()` | Calculates male/female death totals, percentages, and difference |
| `cal_yearly_death()` | Returns yearly death totals with NumPy statistical analysis |

NumPy functions used: `np.mean()`, `np.std()`, `np.median()`, `np.percentile()`

### 📊 Section 3 – Data Handling with Pandas
- Confirmed all 8 columns had correct data types
- Zero null values and zero duplicate rows found in filtered dataset
- Investigated **531 zero-death rows** — confirmed as legitimate data (NHS hospices, Non-NHS hospitals, rare local authority care homes)

### 📈 Section 4 – Data Visualisation
Five charts created with Matplotlib and Seaborn (see below)

### 🖥️ Section 5 – GUI Development
- Built with **Tkinter** using a persistent sidebar and dynamic main panel
- Charts embedded using `FigureCanvasTkAgg`
- `clear_screen()` function prevents widget overlap between views
- 6 navigation buttons: Home Summary, ICB Regions, Places of Death, Gender Split, Yearly Trends, Heatmap

---

## Charts & Visualisations

### Chart 1 – Top 5 ICB Regions by Death Rate
Horizontal bar chart showing the five Integrated Care Board regions with the highest total deaths (2015–2024).

> 📌 NHS North East and North Cumbria leads with **331,234 deaths** — reflecting a large, older population across a vast geographic area.

---

### Chart 2 – Top 5 Places of Death
Pie chart showing the proportion of deaths by location.

> 📌 **NHS hospitals (42.8%)**, private homes (26.1%), and non-local authority care homes (20%) account for **93% of all deaths**.

---

### Chart 3 – Gender Distribution of Deaths
Bar chart comparing total male vs female deaths with percentage labels.

> 📌 Remarkably balanced: **Male 50.03%** vs **Female 49.97%** — a difference of just 3,627 deaths over 10 years.

---

### Chart 4 – Mortality Trend (2015–2024)
Line chart with annual deaths, a 10-year average reference line, and a COVID-19 spike marker for 2020.

> 📌 2020 recorded **569,700 deaths** — the highest in the dataset and **1.9 standard deviations above the 10-year average**, confirming COVID-19 as a genuine statistical outlier.

---

### Chart 5 – Death by Place and Year Heatmap
Seaborn heatmap showing deaths by place of death across each year.

> 📌 NHS hospitals dominate across all years. A clear shift toward home deaths is visible from 2020 onwards, indicating a pandemic-driven change in end-of-life care patterns.

---

## Key Findings

- 🗺️ **Northern England** had the highest concentration of deaths across ICB regions
- 🏥 **NHS hospitals** accounted for 42.8% of all deaths
- 🏠 **Home deaths rose** post-2020, suggesting a lasting shift in end-of-life preferences
- ⚖️ **Gender split** was almost perfectly equal at the national level
- 🦠 **2020 COVID spike** was 1.9 standard deviations above the 10-year mean — a confirmed statistical outlier
- 🔢 531 zero-death rows (~2.9%) were verified as **legitimate data**, not errors

---

## Technologies Used

| Library | Purpose |
|---|---|
| `pandas` | Data loading, filtering, and manipulation |
| `numpy` | Statistical analysis (mean, std, median, percentile) |
| `matplotlib` | Charts and visualisations |
| `seaborn` | Heatmap visualisation |
| `tkinter` | GUI dashboard |
| `openpyxl` | Reading `.xlsx` files |

---


---

## References

| Resource | Link |
|---|---|
| ONS Dataset | https://www.ons.gov.uk |
| NumPy Docs | https://numpy.org |
| Pandas Docs | https://pandas.pydata.org |
| Matplotlib Docs | https://matplotlib.org |
| Seaborn Docs | https://seaborn.pydata.org |
| Tkinter Docs | https://docs.python.org/3/library/tkinter.html |

---

## 👤 Author

**Abhishek Sonawane**  


---

*Data Source: Office for National Statistics (ONS) — Deaths registered in England and Wales, 2024*
