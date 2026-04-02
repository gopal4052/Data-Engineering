# 🏅 Medallion Architecture with PySpark & Delta Lake on Databricks

A scalable, layered data pipeline built using the **Medallion Architecture** (Bronze → Silver → Gold) on **Databricks** with **Apache PySpark** and **Delta Lake**.

---

## 📐 Architecture Overview

```
Raw Data Source
      │
      ▼
┌─────────────┐
│   BRONZE    │  ← Raw ingestion, no transformations
│  (Raw Zone) │
└─────────────┘
      │
      ▼
┌─────────────┐
│   SILVER    │  ← Cleaned, deduplicated, validated
│ (Clean Zone)│
└─────────────┘
      │
      ▼
┌─────────────┐
│    GOLD     │  ← Aggregated, business-ready data
│(Serving Zone)│
└─────────────┘
      │
      ▼
 BI / Analytics / ML
```

---

## 🗂️ Project Structure

```
├── notebooks/
│   ├── 01 retail_sales_analytics_bronze.ipynb      # Raw data ingestion
│   ├── 02 retail_sales_analytics_silver.ipynb        # Cleaning & validation
│   └── 03 retail_sales_analytics_gold.ipynb      # Business-level aggregations
├── data/
│   ├── bronze/                                     # Delta tables - raw
│   ├── silver/                                     # Delta tables - cleaned
│   └── gold/                                       # Delta tables - aggregated
|
└── README.md
```
Other practice notebook file also uploaded.
---

## 🥉 Bronze Layer — Raw Ingestion

- Ingests raw data **as-is** from the source (CSV, JSON, Parquet, APIs, etc.)
- No transformations applied — preserves original data for auditability
- Stored as **Delta tables** for ACID compliance and time travel



## 🥈 Silver Layer — Cleaned & Validated

- Removes duplicates, null values, and malformed records
- Applies schema enforcement and data type casting
- Joins, filters, and standardizes data for downstream use



## 🥇 Gold Layer — Business-Ready Aggregations

- Aggregated, enriched, and ready for BI tools, dashboards, or ML models
- Optimized for query performance using **OPTIMIZE** and **ZORDER**
- Represents business metrics and KPIs



## ⚙️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Apache PySpark** | Distributed data processing |
| **Databricks** | Unified analytics platform |
| **Delta Lake** | ACID-compliant storage layer |
| **Delta Tables** | Versioned, queryable data storage |
| **Databricks DBFS / ADLS** | Cloud storage for Delta tables |

---

## 🚀 How to Run

1. Clone this repository or import notebooks into **Databricks Workspace**
2. Attach notebooks to a running **Databricks cluster**
3. Run notebooks in order:
   - `01 retail_sales_analytics_bronze.ipynb`
   - `02 retail_sales_analytics_silver.ipynb`
   - `03 retail_sales_analytics_gold.ipynb`
4. Query Gold layer tables via **Databricks SQL** or connect to BI tools

---

## ✨ Key Features

- ✅ **ACID Transactions** via Delta Lake
- ✅ **Time Travel** — query previous versions of data
- ✅ **Schema Evolution** — handle changing data structures
- ✅ **Scalable** — runs on distributed Databricks clusters
- ✅ **Modular** — each layer is independently maintainable

---

## 📊 Delta Lake Optimizations Used

```sql
-- Optimize table for faster reads
OPTIMIZE delta.`/mnt/gold/table_name/` ZORDER BY (category, date);

-- Vacuum old files (retain 7 days by default)
VACUUM delta.`/mnt/gold/table_name/` RETAIN 168 HOURS;
```

---

## 👤 Author

**Gopal Sharma**
- GitHub: [github.com/gopal4052](https://github.com/gopal4052)
- LinkedIn: [linkedin.com/in/gopalsharmaaa](https://linkedin.com/in/gopalsharmaaa)

