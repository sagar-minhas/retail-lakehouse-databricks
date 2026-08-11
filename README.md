# Retail Lakehouse Project

A Databricks-based data engineering project for processing retail order data through a Bronze, Silver, and Gold architecture.

## Architecture

**Source Files → Auto Loader → Bronze → Silver → Gold**

The pipeline is scheduled through a Databricks Job so that the notebooks can run automatically.

## Tech Stack

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
├── README.md
└── notebooks/
    ├── 01_bronze_ingestion
    ├── 02_silver_transformation
    └── 03_gold_analytics
```

## Bronze

The Bronze layer ingests the raw order files using Auto Loader.

The data is kept close to the source with only the required ingestion metadata added. Auto Loader schema tracking and checkpoints are used to support incremental processing.

The Bronze data is stored as a Delta table.

## Silver

The Silver layer is where the raw data is cleaned and prepared for downstream use.

The processing includes:

- Cleaning and standardizing source values
- Data quality checks
- Deduplication
- Handling invalid records through quarantine
- Writing the cleaned data to Delta tables

## Gold

The Gold layer contains the business-ready data produced from the validated Silver data.

The current transformations include aggregations used for retail analytics, such as sales, customer, product, and city-level metrics.

## Unity Catalog

The lakehouse is organized in Unity Catalog using separate schemas for each layer:

```text
retail_lakehouse
├── bronze
├── silver
└── gold
```

## Scheduling

The pipeline is scheduled using a Databricks Job. The job runs the processing notebooks automatically instead of requiring them to be started manually.

## GitHub

The project is connected to GitHub through Databricks Git folders.

Changes are developed using feature branches and merged into `main` through pull requests.

## What This Project Covers

- Medallion Architecture
- Incremental ingestion with Auto Loader
- Schema tracking
- Streaming checkpoints
- Delta Lake
- Data cleansing and standardization
- Data quality and quarantine handling
- Deduplication
- Unity Catalog
- Databricks Job scheduling
- Git and GitHub workflow
