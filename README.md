# 📺 Amazon Prime Video Catalog Analysis: Portfolio Optimization Pipeline

## 📌 Project Overview & Domain Context
In the highly competitive Over-The-Top (OTT) streaming and digital entertainment market, subscriber retention and minimizing user churn are directly bound to catalog health and metadata precision. Because content acquisition demands multi-billion-dollar capital allocation, global platforms cannot rely on speculative curation.

This capstone project approaches the Amazon Prime Video catalog as a relational data system. By building a robust data engineering and Exploratory Data Analysis (EDA) pipeline, this project diagnoses catalog composition asymmetries, evaluates international production footprints, maps demographic positioning through audience age certifications, and audits historical content quality trajectories to drive maximum subscriber engagement and platform growth.

---

## 🚀 Key Business Objectives
* **Catalog Evaluation:** Audit the overall structural content composition of the platform.
* **Quality Drivers:** Analyze the distribution and underlying drivers of content quality using audience ratings.
* **Feature Impact Assessment:** Mathematically evaluate how genre diversity, international co-productions, and content age impact final performance.
* **Strategic Roadmap:** Identify operational risks and high-growth opportunities to optimize future licensing budgets and reduce user churn.

---

## 🛠️ Technical Architecture & Stack
* **Development Environment:** Google Colab / Jupyter Notebooks
* **Core Language Engine:** Python
* **Data Manipulation & Processing:** Pandas, NumPy
* **Data Type Reconstruction:** Python `ast` (`literal_eval`)
* **Visualization Frameworks:** Matplotlib, Seaborn (Static & Matrix diagnostics), Plotly (Interactive Spatial breakdowns)

---

## ⚙️ Data Pipeline & Manipulation Workflow
Before deploying visualizations, a strict data cleansing and architectural layout protocol was enforced across **9,871 distinct title records** and **124,179 credits rows**:

1. **Structural Missingness Imputation:** The `seasons` column exhibited an 86.5% null count. Programmatic filtering confirmed this was context-dependent (movies do not have seasons). Imputed movie null values to `0` to protect column integrity without data loss.
2. **Metadata Standardization:** Cleaned the `age_certification` column (65% missingness) by standardizing and mapping all empty strings into a distinct, queryable `'Not Rated'` category to protect parental lock UX variables.
3. **Statistical Imputation:** Replaced missing numerical scores in `imdb_score` and `tmdb_score` using column **Medians** instead of means, preventing outlier skewing and preserving the natural Gaussian shape of the ratings distribution.
4. **Relational Decoupling (De-nesting):** Stringified arrays in `genres` and `production_countries` were parsed into actual Python lists using `ast.literal_eval`. To completely avoid row duplication and the subsequent artificial inflation of statistical averages (the One-to-Many explosion trap), independent lookup **Dimension Tables** (`Country_table` and `Genre_table`) were engineered, mapping back to the primary titles master sheet via unique IDs.

---

## 📊 Core Analytical Insights

* **The Catalog Asymmetry Trap:** The inventory shows a steep structural bottleneck dominated by Movies (**86.2%**) relative to TV Shows (**13.8%**). Since serialized shows drive weekly recurring user habits and platform loyalty, over-indexing on standalone movies represents an immediate customer retention risk.
* **Stable Quality Baseline:** Overlaying a Kernel Density Estimate (KDE) line over rating distributions exposed a clean Gaussian curve centered around a **6.1 median IMDb score**, showing a highly uniform mid-tier repository but a clear scarcity of premium masterpieces.
* **The Regional Powerhouse:** Interactive spatial tracking isolated **India (IN)** as the fastest-growing and highest-performing production footprint outside the United States, representing a prime international expansion hub.
* **The Myth of 'Genre Packing':** An annotated Pearson correlation matrix mathematically proved that an asset's total `genre_count` has a near-zero relationship (**$r \approx 0.02$**) with final user scores, proving that stuffing content with excessive tags does not improve user satisfaction.

---

## 💡 Strategic Recommendations for Leadership
1. **Pivot to Originals:** Reallocate future capital expenditure away from bulk standalone movies and pivot heavily toward multi-season **Original Serialized TV Shows** to cultivate long-term user habits and stop subscription churn.
2. **Double Down on India:** Prioritize infrastructure and content licensing budgets within the Indian market to capture high-growth emerging demographics.
3. **Metadata Hygiene Sprint:** Systematically clean and audit the 6,400+ `'Not Rated'` placeholder assets to ensure parental control filters function flawlessly for family-tier subscribers.
4. **Precision Micro-Tagging:** Eliminate misleading 'genre packing' and adopt a precision, audience-centric micro-tagging framework to optimize the training data feeding the platform's recommendation engine.

---

## 🔮 Future Scope & Engineering Roadmap
* **Executive Dashboarding:** Migrate the engineered relational data structures into an interactive Tableau/Power BI dashboard for real-time stakeholder reporting.
* **Predictive Modeling:** Construct a Machine Learning pipeline (Random Forest / XGBoost) to predict a title's potential audience rating *prior* to platform acquisition based on historical cast, crew, and genre combinations.
* **Natural Language Processing (NLP):** Apply sentiment analysis and text-mining models on the textual `description` attributes to automate semantic content categorization.
