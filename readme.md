# Anime & Manga Data Analytics Pipeline

## Project Overview
This repository contains an end-to-end Exploratory Data Analysis (EDA) and data preprocessing pipeline for a comprehensive dataset of over 25,000 anime and manga records. The project is broken down into a modular, three-step workflow focusing on rigorous data cleansing, statistical inference, and explanatory data visualization. 

The primary objective is to transform raw, heavily tagged media data into structured formats, uncover structural drivers behind community engagement, and prepare the dataset for downstream machine learning modeling.

---

## Repository Structure

The analytical pipeline is divided into three core Jupyter Notebooks:

### 1. `data_cleaning.ipynb`
This notebook handles the initial ingestion and structural formatting of the raw dataset. 
* **Missing Value Imputation:** Identifies structural zeros (e.g., `Score = 0.00` for unrated titles) and explicitly converts them to `NaN` to prevent artificial variance reduction and mean-imputation bias in future ML models.
* **Hierarchical Index Flattening:** Re-structures multi-level indices generated during multi-variable `groupby` operations (e.g., `["Genres", "Episodes"]`) back into flat, model-ready DataFrames using `.reset_index()`.
* **High-Cardinality Management:** Processes complex, comma-separated fields to isolate target variables.

### 2. `Stats.ipynb`
This notebook focuses on descriptive statistics and resolving data fragmentation.
* **Aggregation Pipelines:** Utilizes Pandas `.agg()` functions to simultaneously extract the minimum, maximum, and sample size (`count`) of highly specific subgroups.
* **Statistical Significance Filtering:** Implements custom masks to filter out production entities with low sample sizes (e.g., isolating studios with a minimum threshold of 10 productions) to ensure that calculated means reflect true performance rather than isolated anomalies.
* **Correlation Mapping:** Investigates linear relationships between engagement metrics like `Popularity`, `Favorites`, and `Members`.

### 3. `visualization.ipynb`
This notebook leverages Matplotlib and Pandas plotting to translate the statistical findings into clear visual narratives.
* **Categorical Performance:** Generates bar charts analyzing the average scores of anime based on their underlying `Source` material (Manga, Light Novel, Original, etc.).
* **Studio Power Rankings:** Visualizes the Top 20 highest-rated production studios, cleanly formatted with optimized figure sizing and custom grid layouts for readability.

---

## Dataset Details
The dataset encompasses a rich mix of continuous, categorical, and text data:
* **Target Metrics:** `Score` (User ratings), `Popularity` (Global rank), `Favorites` (User bookmark counts).
* **Categorical Features:** `Studios` (Production houses), `Source` (Origin material), `Type` (TV, Movie, OVA).
* **Quantitative Features:** `Episodes` (Total length), `Members` (Total community reach).

---

## Core Analytical Insights

1. **The Engagement Loop:** A powerful positive correlation exists between
