# **Project Title: Anime & Manga Data Analytics & Predictive Modeling**

## **Project Overview**
This project delivers an end-to-end Exploratory Data Analysis (EDA) and data cleaning pipeline executed on a comprehensive dataset containing over **25,000 rows** of anime and manga records. The objective of this study was to transform raw, scrape-heavy, multi-tagged media data into a structured format suitable for statistical inference and machine learning algorithms. By isolating features such as production studios, source materials, episode lengths, and community engagement metrics, this project uncovers the structural drivers behind critical success metrics like user scores and overall popularity.

---

## **Dataset & Key Features**
The dataset encompasses a rich combination of categorical, continuous, and unstructured text fields:
* **Target/Success Metrics:** `Score` (Continuous user ratings), `Popularity` (Ordinal global rank), `Favorites` (Total user bookmark counts).
* **Categorical Features:** `Studios` (Production houses), `Source` (Manga, Light Novel, Original, Game), `Type` (TV, Movie, OVA).
* **Quantitative Features:** `Episodes` (Total length), `Members` (Total community reach/subscriber base).
* **Text Features:** `Synopsis` (Narrative summaries for NLP features).

---

## **Technical Methodology & Pipeline**

### **1. Data Cleansing & Advanced Missing Value Handling**
* **Placeholder Isolation:** Identified hidden missing values masking as structural zeros (e.g., `Score = 0.00` for unreleased or unrated titles).
* **NaN Transitioning:** Converted arbitrary zero-placeholders to true `NaN` values to protect downstream machine learning pipelines from artificial variance reduction and mean-imputation bias.
* **High-Cardinality Management:** Handled complex, comma-separated string fields within the `Genres` and `Studios` columns to avoid data fragmentation during feature grouping.

### **2. Statistical Significance Filtering**
* **Outlier & Singleton Mitigation:** Built custom aggregation masks to filter out production groups with low sample sizes (e.g., studios with fewer than 10 productions) ensuring that calculated means reflect true structural performance rather than isolated data anomalies.

### **3. Explanatory Data Visualization**
* Leveraged **Pandas**, **Matplotlib**, and **Seaborn** to build multi-dimensional aggregations, categorical distributions, and linear relationship models.

---

## **Core Insights & Statistical Findings**

Based on the final exploratory phase and the feature correlation matrix, several key phenomena were uncovered:

### **The Engagement Loop (Strong Positive Correlation)**
* A powerful positive correlation (**~0.78**) exists between `Members` and `Favorites`. This indicates that community size scales predictably with hardcore fan dedication; as a show's general tracking audience grows, its dedicated fanbase expands linearly.

### **The Popularity Rank Paradox (Negative Correlation)**
* A noticeable negative correlation exists between `Score` and `Popularity` (approximately **-0.42**). Because the `Popularity` column represents a *rank* (where Rank 1 is the most popular), this negative coefficient proves a mathematically robust truth: **higher user scores correlate strongly with a lower rank number (closer to Rank 1).**

### **The Episode Count Neutrality**
* The correlation between `Episodes` and `Score` is exceptionally weak (approximately **0.10**). This demonstrates that a show’s length has virtually no baseline linear impact on its quality or critical reception; short-form seasonal series and massive long-running epics compete on an equal playing field regarding user satisfaction.

---

## **Technologies Used**
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
