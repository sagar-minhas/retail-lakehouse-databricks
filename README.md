# Retail Lakehouse Project

An end-to-end data engineering project built using Databricks, PySpark, Delta Lake, and Unity Catalog. The project follows a Medallion Architecture to incrementally ingest, clean, validate, transform, and publish retail order data.

## Architecture

```text
Source CSV Files
       |
       v
  Auto Loader
       |
       v
    BRONZE
       |
       | Cleaning & Validation
       v
    SILVER
       |
       | Business Transformations
       v
     GOLD
       |
       v
Databricks Job
   / Schedule
```

## Technology Stack

- Databricks
- PySpark
- Python
- Delta Lake
- Unity Catalog
- Auto Loader
- Databricks Jobs
- GitHub

## Project Structure

```text
retail-lakehouse-databricks/
│
├── README.md
│
└── notebooks/
    ├── 01_bronze_ingestion
    ├── 02_silver_transformation
    └── 03_gold_analytics
```

## Data Pipeline

### Bronze Layer

The Bronze layer ingests raw retail order files using Databricks Auto Loader.

Key capabilities:

- Incremental file ingestion
- Schema tracking
- Streaming checkpoints
- File-level metadata
- Delta Lake storage

The Bronze layer keeps the ingested data close to its original form so that source information can be retained and reprocessed when required.

### Silver Layer

The Silver layer transforms Bronze data into clean and validated datasets.

Processing includes:

- Data cleansing
- Standardization of source values
- Data quality validation
- Deduplication
- Quarantine handling for invalid records

The resulting datasets are stored as Delta tables.

### Gold Layer

The Gold layer contains business-ready datasets derived from the validated Silver data.

The layer supports analytical use cases and business KPIs including aggregations around:

- Sales
- Customers
- Products
- Cities

## Data Organization

The project uses Unity Catalog to organize the lakehouse:

```text
retail_lakehouse
├── bronze
│   └── orders_bronze
├── silver
│   └── curated tables
└── gold
    └── business-ready tables
```

## Orchestration

The pipeline is automated using a Databricks Job with scheduling.

The workflow executes the processing notebooks automatically instead of relying on manual notebook execution.

## Version Control

The project is integrated with GitHub using Databricks Git folders.

Development follows a feature-branch and pull-request workflow:

```text
main
  |
  +-- feature/<change>
          |
        Commit
          |
         Push
          |
    Pull Request
          |
        Review
          |
        Merge
          |
         main
```

This provides version history, controlled development, and code review before changes are merged into the main branch.

## Key Engineering Concepts

- Medallion Architecture
- Incremental data ingestion
- Auto Loader
- Schema tracking and evolution
- Streaming checkpoints
- Delta Lake
- Data quality and quarantine handling
- Deduplication
- Unity Catalog
- Databricks Jobs and scheduling
- Git-based development and pull requests
