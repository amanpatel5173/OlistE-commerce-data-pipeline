# End-to-End Azure Data Engineering Pipeline

## Olist E-Commerce Dataset

---

# Project Overview

This project demonstrates the design and implementation of an **end-to-end cloud data engineering pipeline** using the **Olist E-commerce dataset**.

The pipeline ingests raw transactional data, stores it in a **data lake**, processes it using distributed computing, and prepares analytics-ready datasets for business intelligence tools.

The architecture follows a **modern data engineering workflow using Azure services**, enabling scalable data ingestion, transformation, storage, and analytics.

This project simulates a **real-world enterprise data platform** used by e-commerce companies to analyze sales, customer behavior, and operational performance.

---

# Problem Statement

E-commerce platforms generate massive amounts of transactional data such as orders, payments, customers, sellers, and product information. This data often exists in multiple systems and formats, making it difficult for analysts and business teams to derive meaningful insights.

The objective of this project is to design and implement a **scalable data pipeline** that:

• Ingests raw e-commerce datasets from external sources
• Stores the data in a centralized cloud data lake
• Cleans and transforms the data using distributed processing
• Creates structured datasets optimized for analytics
• Enables business intelligence dashboards and reporting

The pipeline demonstrates how raw operational data can be transformed into **decision-ready analytical data**.

---

# Architecture Diagram

The following diagram illustrates the **end-to-end data pipeline architecture** used in this project.
![Architecture Diagram](Architecture%20Diagram.png)

---

# Pipeline Explanation

The data pipeline is composed of several stages that transform raw data into analytics-ready datasets.

### 1. Data Sources

The pipeline begins with raw datasets obtained from:

• GitHub hosted datasets
• SQL tables

These sources contain e-commerce transaction data including customers, orders, products, sellers, payments, and reviews.

---

### 2. Data Ingestion (Azure Data Factory)

Azure Data Factory is used to orchestrate the **data ingestion pipelines**.

Responsibilities include:

• Extracting data from source systems
• Automating ingestion workflows
• Loading raw datasets into Azure Data Lake Storage

This stage ensures reliable and repeatable data ingestion.

---

### 3. Raw Data Storage (ADLS Gen2)

The ingested datasets are stored in **Azure Data Lake Storage Gen2**.

This layer stores the **raw unprocessed data** and acts as the foundation of the data lake.

Benefits include:

• Scalable cloud storage
• Separation of compute and storage
• Centralized data repository

---

### 4. Data Transformation (Azure Databricks)

Azure Databricks is used to process and transform the data using **PySpark**.

Key transformations include:

• Data cleaning and preprocessing
• Handling missing values
• Joining multiple datasets
• Standardizing schemas
• Feature engineering

Databricks enables distributed processing for handling large datasets efficiently.

---

### 5. Data Enrichment (MongoDB)

MongoDB is used as a **NoSQL enrichment layer**.

Additional lookup tables or enrichment datasets can be stored in MongoDB and integrated during the transformation process.

This demonstrates integration between **SQL and NoSQL data sources** in modern data pipelines.

---

### 6. Processed Data Storage (ADLS Gen2)

After transformation, the processed datasets are written back to **Azure Data Lake Storage**.

This layer contains **cleaned and structured data** ready for analytical querying.

---

### 7. Data Warehousing (Azure Synapse Analytics)

Azure Synapse Analytics is used as the **analytical query engine**.

External tables and views are created to query transformed datasets stored in the data lake.

This enables:

• High-performance SQL analytics
• Data warehouse style queries
• Integration with BI tools

---

### 8. Data Visualization

The final datasets are connected to visualization tools such as:

• Power BI
• Tableau
• Microsoft Fabric

These tools enable creation of dashboards and business insights such as:

• Sales trends
• Customer purchasing patterns
• Top performing products
• Seller performance analysis

---

# Tech Stack

| Technology                   | Purpose                                           |
| ---------------------------- | ------------------------------------------------- |
| Azure Data Factory           | Data ingestion and pipeline orchestration         |
| Azure Data Lake Storage Gen2 | Scalable cloud storage for raw and processed data |
| Azure Databricks             | Distributed data processing                       |
| PySpark                      | Data transformation and processing                |
| MongoDB                      | NoSQL data enrichment                             |
| Azure Synapse Analytics      | Analytical querying and data warehousing          |
| SQL                          | Data analysis queries                             |
| Power BI / Tableau / Fabric  | Data visualization                                |

---

# Project Structure

```
OlistE-commerceproject
│
├── data
│   └── raw
│       ├── olist_customers_dataset.csv
│       ├── olist_geolocation_dataset.csv
│       ├── olist_order_items_dataset.csv
│       ├── olist_order_payments_dataset.csv
│       ├── olist_order_reviews_dataset.csv
│       ├── olist_orders_dataset.csv
│       ├── olist_products_dataset.csv
│       ├── olist_sellers_dataset.csv
│       └── product_category_name_translation.csv
│
├── notebooks
│   ├── Adls to databricks.ipynb
│   └── DataIngestionToDB.ipynb
│
├── sql
│   └── sql code.txt
│
├── Olist_datadb
│   └── Dataingestiontosql.ipynb
│
├── images
│   └── architecture.png
│
└── README.md
```

---

# Key Data Engineering Concepts Demonstrated

• End-to-end cloud data pipeline design
• Data Lake architecture
• Distributed data processing with Spark
• ETL / ELT pipeline implementation
• SQL-based analytical querying
• Integration with NoSQL databases
• Data visualization and BI integration

---

# Author

**Aman Patel**
B.Tech IT — IIIT Vadodara
Aspiring Data Engineer

---
