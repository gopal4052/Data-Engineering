# Data-Engineering

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
