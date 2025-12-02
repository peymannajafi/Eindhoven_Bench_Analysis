# 🏞️ Eindhoven Public Bench Geospatial and Distribution Analysis

## Project Overview

This project analyzes the distribution and characteristics of public benches in the city of Eindhoven, Netherlands, using a dataset provided by the municipal government.

The analysis is divided into two parts: a **statistical distribution analysis** and a **geospatial clustering analysis** using DBSCAN.

## 📊 Key Findings

The analysis of 4,000+ benches revealed a highly concentrated and non-uniform public seating strategy in Eindhoven:

* **High Concentration:** Benches are **not** evenly distributed across the city.
    * The **Gini Coefficient** for benches-per-street was calculated at **0.569**, indicating high inequality in distribution.
    * Approximately **81%** of all benches are located in just two categories: **"Park"** and **"Plein" (Square)**.

* **Spatial Clustering (DBSCAN):**
    * Using a 100-meter radius, **133 distinct seating clusters** were identified.
    * A significant portion of the total dataset (~40%) was classified as **"noise"** (isolated benches), suggesting many benches are scattered along paths rather than tightly grouped.
    * One major cluster contained **144 benches**, highlighting the use of single, high-volume social nodes.

* **Temporal Spikes:**
    * The data shows an overwhelming installation spike, with over **1,200 benches installed in the single year 2006**, suggesting a major, coordinated city-wide infrastructure project.

## 🔬 Methodology

### 1. Statistical Analysis (`Zitbanken_analysis.ipynb`)

* **Data Exploration:** Initial checks on unique street counts and top locations.
* **Concentration Metrics:** Calculated the total count and percentage of benches located in the top 5 locations.
* **Inequality Measure:** Used the **Gini Coefficient** to quantify the unevenness of the bench-per-street distribution.

### 2. Geospatial Clustering (`zitbanken_geoanalysis.ipynb`)

* **Geospatial Preparation:** Converted string coordinates to numeric, and projected the data from the geographic **EPSG:4326** system to the metric **EPSG:28992 (Dutch RD New)** CRS for accurate distance calculations.
* **DBSCAN Implementation:** Used the Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm with an epsilon ($\epsilon$) of **100 meters** and a minimum of **7 samples** per cluster ($\text{MinPts}=7$).
* **Cluster Characterization:** Determined the size and primary `LOCATIE` (using the mode) for each identified cluster.
* **Visualization:** Generated spatial plots to visualize the resulting clusters and noise points on a map.

## 🛠️ Required Libraries

This project requires the following Python libraries. You can install them using the command: `pip install -r requirements.txt`

The libraries are listed in the `requirements.txt` file below.
