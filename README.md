# SmartShift AI 🇮🇳

> **AI-powered city relocation intelligence for India** — helping professionals make smarter, data-driven decisions about where to live and work across 116+ Indian cities.

---

## 📌 Overview

**SmartShift AI** is a data science project that analyses cost of living, quality of life, and financial viability across Indian cities to help individuals and organisations make informed relocation decisions.

By combining two real-world datasets — city-level living costs and quality-of-life indicators — and applying feature engineering alongside unsupervised machine learning (K-Means clustering), SmartShift AI produces actionable city profiles grouped by affordability and livability.

---

## 🎯 Problem Statement

Relocating for work in India is complex. A higher salary in Mumbai or Delhi doesn't automatically translate to a better standard of living once rent, food, internet, safety, and healthcare are factored in. SmartShift AI answers the question:

> **"Given my income, which Indian cities offer the best quality of life for the money?"**

---

## 🗂️ Project Structure

```
SmartShift-AI/
│
├── data/
│   ├── raw/                        # Original source datasets
│   │   ├── india_cost_quality_dataset.csv
│   │   └── livingcost_india_all_inr.csv
│   └── processed/                  # Cleaned & merged datasets
│       └── india_cost_quality_merged.csv
│
├── notebooks/                      # Jupyter analysis notebooks
│   ├── 01_data_inspection.ipynb
│   ├── 02_master_dataset_inspection.ipynb
│   ├── 03_data_Integration.ipynb
│   ├── 04_EDA.ipynb
│   └── 05_ML_modeling.ipynb
│
├── notebooks_markdown/             # Markdown exports of notebooks
│   ├── 01_data_inspection.md
│   ├── 02_master_dataset_inspection.md
│   ├── 03_data_Integration.md
│   ├── 04_EDA.md
│   └── 05_ML_modeling.md
│
├── visualizations/                 # Generated charts and plots
│   ├── outliers/
│   ├── distributions/
│   └── correlations/
│
├── models/                         # Saved model artefacts
├── src/                            # Source modules (future)
├── docs/                           # Project documentation
├── requirements.txt
└── README.md
```

---

## 📊 Datasets

| Dataset | Records | Key Features |
|---|---|---|
| `india_cost_quality_dataset.csv` | 170 cities | Rent, food cost, internet speed, healthcare rating, safety score, happiness index |
| `livingcost_india_all_inr.csv` | — | Monthly cost of living (1 person), rent, salary estimates (all in INR) |

### Merged Dataset — `india_cost_quality_merged.csv`

After integration and feature engineering, the master dataset contains **116 cities × 14 features**:

| Feature | Description |
|---|---|
| `City` | Indian city name |
| `Average Rent (INR/month)` | Average monthly rent |
| `Food Cost (INR/month)` | Average monthly food expenses |
| `Internet Speed (Mbps)` | Average broadband speed |
| `Healthcare Rating` | Healthcare quality score (0–10) |
| `Safety Score` | Safety index (0–10) |
| `Happiness Index` | Subjective happiness score (0–10) |
| `months_covered` | Salary expressed in months of living cost |
| `cost_one_person_inr` | Total estimated monthly cost (1 person) |
| `rent_one_person_inr` | Estimated rent from living cost dataset |
| `monthly_salary_after_tax_inr` | Estimated post-tax monthly salary |
| `income_after_rent_inr` | Disposable income after rent |
| `rent_difference_inr` | Difference between rent sources |
| `rent_difference_percent` | Relative rent gap (%) |

---

## 🔬 Analysis Pipeline

The project is structured as a sequential series of Jupyter notebooks:

### `01` — Data Inspection
Initial exploration of the raw quality-of-life dataset (170 cities, 7 columns). Verified data types, checked for nulls and duplicates — the dataset was clean with zero missing values.

### `02` — Master Dataset Inspection
Deep inspection of the living cost dataset covering salary estimates, rent and cost-of-living figures across Indian cities.

### `03` — Data Integration & Feature Engineering
- Merged the two datasets on city name (inner join → 116 cities)
- Engineered derived features:
  - `income_after_rent_inr` — disposable income proxy
  - `rent_difference_inr` / `rent_difference_percent` — cross-source rent comparison
  - `months_covered` — affordability ratio

### `04` — Exploratory Data Analysis (EDA)

**Univariate Analysis:**
- Average rent is **right-skewed** — most cities sit in ₹4k–₹10k; metro outliers (Mumbai ₹34,896/mo) are extreme
- Food cost is **roughly normally distributed** across ₹3k–₹8k
- Quality scores (Healthcare, Safety, Happiness) are bounded and well-spread

**Outlier Detection (IQR method):**

| Feature | Outlier Count |
|---|---|
| `rent_difference_inr` | 13 |
| `rent_one_person_inr` | 11 |
| `Average Rent (INR/month)` | 11 |
| `cost_one_person_inr` | 8 |

**Correlation Highlights:**
- `monthly_salary_after_tax_inr` ↔ `income_after_rent_inr` → **0.87** (strong positive)
- `Average Rent` ↔ `income_after_rent_inr` → **−0.49** (higher rent = less disposable income)
- `Average Rent` ↔ `rent_one_person_inr` → **0.42** (moderate cross-source agreement)

**Key Finding:** Several cities show a **negative `income_after_rent_inr`** — estimated post-tax salary cannot cover rent alone. These cities represent financially unviable relocation targets for average earners.

### `05` — ML Modelling — K-Means City Clustering

**Goal:** Discover natural city segments from cost + quality-of-life features using unsupervised learning.

**Features used for clustering:**
- `cost_one_person_inr`
- `Average Rent (INR/month)`
- `Food Cost (INR/month)`
- `Internet Speed (Mbps)`
- `Healthcare Rating`
- `Safety Score`
- `Happiness Index`

**Methodology:**

```
116 Cities → StandardScaler → K-Means (k=2 to k=8)
                                      ↓
              Elbow Method + Silhouette Score → Best k=2
                                      ↓
                          Final City Cluster Profiles
```

**Elbow + Silhouette Results:**

| k | Inertia | Silhouette Score |
|---|---|---|
| 2 | 683.27 | **0.298** ✅ Best |
| 3 | 589.29 | 0.149 |
| 4 | 534.92 | 0.146 |
| 5 | 486.22 | 0.146 |
| 6 | 445.75 | 0.154 |
| 7 | 417.67 | 0.149 |
| 8 | 386.52 | 0.155 |

**k=2** was selected based on the highest silhouette score.

**Final Cluster Profiles:**

| Cluster | Characteristic | Avg Rent | Avg Internet | Example Cities |
|---|---|---|---|---|
| **Cluster 0** — Premium Metros | High rent, fast internet, higher salaries | ₹19,541 | 114 Mbps | Mumbai, Delhi, Bengaluru, Hyderabad, Chennai |
| **Cluster 1** — Affordable Cities | Lower cost, broad salary range | ₹6,841 | 82 Mbps | Jaipur, Indore, Lucknow, Surat, Nagpur |

---

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.10+
- Jupyter Lab / Jupyter Notebook

### Installation

```bash
# Clone the repository
git clone https://github.com/YUVRAJRANA10/SmartShift-AI.git
cd SmartShift-AI

# Create and activate virtual environment
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Running the Notebooks

```bash
jupyter lab
```

Open the notebooks in order from `notebooks/01_data_inspection.ipynb` through `notebooks/05_ML_modeling.ipynb`.

---

## 📦 Key Dependencies

| Package | Version | Purpose |
|---|---|---|
| `pandas` | 3.0.5 | Data manipulation |
| `numpy` | 2.5.1 | Numerical computing |
| `scikit-learn` | 1.9.0 | K-Means, StandardScaler, silhouette score |
| `matplotlib` | 3.11.1 | Visualisation |
| `seaborn` | 0.13.2 | Statistical plots |
| `jupyterlab` | 4.6.2 | Notebook environment |

---

## 📈 Key Findings

- 🏙️ **Metro cities** (Mumbai, Delhi, Bengaluru) form a distinct high-cost, high-connectivity cluster — they are **not always the best value** relative to income
- 💸 **Mumbai shows negative disposable income** — average post-tax salary cannot cover the estimated rent
- 🌆 **Tier-2 cities** (Indore, Jaipur, Lucknow, Mysuru) score comparably on healthcare and happiness at a fraction of the cost
- 📡 **Internet speed** is a key differentiator for the premium metro cluster (114 Mbps avg vs 82 Mbps for tier-2)
- 🏥 **Healthcare & Happiness scores are not strongly correlated with rent** — expensive cities don't always offer a better quality of life

---

## 🔭 Roadmap

- [ ] Build a **city recommendation engine** — input salary + preferences → ranked city suggestions
- [ ] Add an **interactive dashboard** (Streamlit / Plotly Dash) for visual city comparison
- [ ] Expand dataset to **250+ cities** with additional data sources
- [ ] Incorporate **job market data** — average salaries by sector per city
- [ ] Add **commute time & infrastructure scores** as additional clustering features
- [ ] Experiment with **DBSCAN / hierarchical clustering** as alternatives to K-Means

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or pull requests for:
- Additional datasets or data sources
- New feature engineering ideas
- Dashboard / UI improvements
- Bug fixes or refactoring

---

## 📄 Licence

This project is open source. Data sources are publicly available cost-of-living datasets compiled for research purposes.

---

<div align="center">

**Built with ❤️ by [Yuvraj Rana](https://github.com/YUVRAJRANA10)**

*Making data-driven relocation decisions accessible for everyone in India.*

</div>
