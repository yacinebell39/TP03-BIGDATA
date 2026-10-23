# TP03: Interactive Data Analysis and Visualization with Power BI

**Module:** Big Data Analytics  
**Academic Year:** 2026/2027  
**Institution:** University of Eloued - Faculty of Exact Sciences, Department of Computer Science  
**Target:** Second-year Master: IA & Data Science  
**Dataset:** Safecast Radiation Dataset (`safecast_5gb`)  

---

## 1. Executive Summary & Lab Findings (5–8 Lines)

1. **Massive Scale & Baseline KPI:** The imported and cleansed Safecast dataset encompasses approximately **15 million records** (`15M`), accurately calculated using DAX measure `COUNTROWS('safecast_5gb')`.
2. **Dominant Unit of Measurement:** The horizontal bar chart reveals that **`cpm`** (counts per minute) is the overwhelming primary unit (>12M readings), followed secondarily by sensor operational status and ambient temperature (`celcius`).
3. **Sensor Disparity & Top Contributors:** Categorical filtering of the top 10 recording devices reveals severe data skew, led dominantly by device ID `65002` (>1.2M readings), reflecting primary long-running fixed monitoring stations.
4. **Spatial Concentration:** The interactive world map illustrates heavy radiation measurement density concentrated in **East Asia (Japan)**, **North America**, and **Western Europe**, aligning with historical post-Fukushima citizen-science sensor deployment networks.
5. **Temporal Daily Patterns:** The daily time-series line chart demonstrates robust, stable logging behavior fluctuating between 140K and 180K measurements per day throughout the month, dropping sharply only on day 31 due to month-length variance.
6. **Cross-Filtering Interactivity:** Integration of the `unit` slicer dynamically updates the KPI card, geographical coordinates, and sensor distributions simultaneously, enabling targeted micro-investigations across sensor modalities.

---

## 2. Visualizations Breakdown

| Visual Component | Type | Fields / Dimensions Applied | Key Insight |
| :--- | :--- | :--- | :--- |
| **KPI Card** | Single Value Card | `Total Measurements` (DAX Measure) | Summarizes the total record count (`15M`). |
| **Bar Chart** | Stacked Horizontal Bar | **Y-axis:** `unit`<br>**X-axis:** `Total Measurements` | Demonstrates reliance on raw Geiger tube pulse rates (`cpm`). |
| **Column Chart** | Clustered Column | **X-axis:** `device_id` (Top 10)<br>**Y-axis:** `Total Measurements` | Identifies critical and active monitoring nodes. |
| **Geographic Map**| Microsoft Bing Map | **Coordinates:** `latitude`, `longitude`<br>**Bubble size:** `Total Measurements` | Maps global radiation measurement coverage. |
| **Line Chart** | Time Series Line | **X-axis:** `Day` (1–31)<br>**Y-axis:** `Total Measurements` | Evaluates streaming continuity and day-to-day log stability. |
| **Slicer** | Interactive Control | `unit` | Provides real-time dynamic dashboard cross-filtering. |

---

## 3. Implemented DAX Formula

```dax
Total Measurements = COUNTROWS('safecast_5gb')
```

---

## 4. Deliverables Checklist
- [x] Power BI Report file: `TP03_PowerBI_Report.pbix`
- [x] Screenshot of data exploration and cleaning in Power Query (`Task1_Import_Data.png`)
- [x] Final interactive dashboard screenshot (`Final_Dashboard.png`)
- [x] Analytical summary report (`README.md`)