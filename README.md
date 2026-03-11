# End-to-End Azure Data Engineering Pipeline

## Olist E-Commerce Dataset

---

# Project Overview

This project demonstrates the implementation of an **end-to-end cloud data engineering pipeline** using the Olist E-commerce dataset. The pipeline ingests raw transactional data, stores it in a cloud data lake, processes it using distributed computing, and prepares analytics-ready datasets for business intelligence tools.

The system is built using **Azure Data Engineering services** and follows modern data platform principles including **Medallion Architecture, metadata-driven pipelines, and parameterized ingestion pipelines**.

The objective is to simulate a **real-world enterprise data pipeline** capable of handling large volumes of e-commerce data and enabling analytical insights.

---

# Problem Statement

E-commerce platforms generate large volumes of data such as customer information, orders, product details, seller data, payments, and reviews. These datasets are typically stored in multiple systems and formats, making it difficult for organizations to perform analytics efficiently.

The goal of this project is to design and implement a **scalable data pipeline** that:

• Ingests raw datasets from external sources
• Stores the data in a centralized cloud data lake
• Transforms raw data into structured datasets
• Builds an analytical data model for reporting
• Enables business intelligence dashboards for insights

The final pipeline enables **efficient analytical queries for business decision making**.

---

# Architecture Diagram

The following diagram illustrates the **end-to-end architecture of the data pipeline**.

![Architecture Diagram](Architecture%20Diagram.png)

---

# Pipeline Explanation

The pipeline consists of multiple stages responsible for ingesting, processing, and analyzing data.

### 1 Data Sources

The pipeline ingests datasets from:

• GitHub hosted datasets
• SQL tables

These datasets include information related to customers, orders, products, sellers, payments, and reviews.

---

### 2 Data Ingestion (Azure Data Factory)

Azure Data Factory is used to orchestrate the **data ingestion pipelines**.

Responsibilities include:

• Extracting datasets from source systems
• Automating ingestion workflows
• Loading datasets into Azure Data Lake Storage

The ingestion pipelines are designed to be **parameterized and metadata-driven** to handle multiple datasets dynamically.

---

### 3 Raw Data Storage (ADLS Gen2)

The ingested data is stored in **Azure Data Lake Storage Gen2**.

This layer stores **raw unprocessed data** and acts as the central storage system for the pipeline.

Benefits include:

• Scalable storage
• Separation of compute and storage
• Cost-efficient large data storage

---

### 4 Data Transformation (Azure Databricks)

Azure Databricks processes the raw datasets using **PySpark**.

Key transformations include:

• Data cleaning
• Handling missing values
• Joining datasets
• Feature engineering
• Schema standardization

The transformed datasets are written back to the data lake.

---

### 5 Data Enrichment (MongoDB)

MongoDB is used as a **NoSQL enrichment layer**.

Additional enrichment tables can be stored in MongoDB and integrated during the transformation process to enhance analytical datasets.

---

### 6 Processed Data Storage (ADLS Gen2)

After transformation, processed datasets are stored back into **Azure Data Lake Storage**.

This layer contains **cleaned and structured datasets ready for analytical processing**.

---

### 7 Data Warehousing (Azure Synapse Analytics)

Azure Synapse Analytics is used to query transformed datasets stored in the data lake.

External tables and views are created to enable:

• Analytical SQL queries
• Integration with BI tools
• Efficient reporting

---

### 8 Data Visualization

The final datasets are connected to visualization tools such as:

• Power BI
• Tableau
• Microsoft Fabric

These tools allow analysts to create dashboards and derive business insights.

---

# Data Architecture (Medallion Architecture)

The pipeline follows the **Medallion Architecture**, which organizes data into multiple layers for improved data quality and analytics.

### Bronze Layer – Raw Data

• Stores raw ingested datasets
• Data is stored without transformation
• Provides traceability and reproducibility

---

### Silver Layer – Cleaned Data

• Data is cleaned and standardized
• Data quality checks are performed
• Multiple datasets are joined

Examples of transformations:

• Handling missing values
• Standardizing schema formats
• Joining customer, order, and product data

---

### Gold Layer – Analytical Data

• Data is optimized for analytics and reporting
• Aggregated and structured tables are created
• Used directly by BI tools

---

# Data Modeling Approach

The analytical layer uses a **Star Schema data model**, which is commonly used in analytical data warehouses.

### Fact Table

The central **fact table** contains transactional data such as:

• Order transactions
• Payment amounts
• Order quantities

Example Fact Table:

**Fact_Orders**

Measures:

• Order value
• Payment amount
• Quantity ordered

---

### Dimension Tables

Dimension tables provide descriptive attributes for analytical queries.

Examples include:

**Dim_Customers**
Customer details and location information

**Dim_Products**
Product categories and product details

**Dim_Sellers**
Seller information and seller location

**Dim_Date**
Date attributes used for time-based analysis

---

### Benefits of Star Schema

• Faster analytical queries
• Simplified joins
• Optimized for BI tools and dashboards

---

# Parameterized Pipeline

The ingestion pipelines are implemented as **parameterized pipelines**.

Parameters used include:

• Dataset name
• Source file path
• Target storage path
• Table name

Benefits:

• Reduces pipeline duplication
• Improves scalability
• Simplifies onboarding of new datasets

---

# Metadata-Driven Pipeline

The pipeline uses a **metadata-driven design** to dynamically process datasets.

Metadata information such as:

• Dataset name
• Source location
• File format
• Target table

is stored in the configuration file:

`dataForEachInput.json`

The pipeline reads this metadata and dynamically processes datasets.

Advantages include:

• Centralized configuration
• Dynamic pipeline execution
• Easy integration of new datasets

---

# Slowly Changing Dimensions (SCD)

The project incorporates **Slowly Changing Dimension (SCD)** concepts for handling changes in dimension data.

This allows the system to track historical changes in attributes such as:

• Customer details
• Product information
• Seller attributes

By maintaining historical records, analysts can perform **trend analysis and historical reporting**.

---

# Tech Stack

| Technology                   | Purpose                     |
| ---------------------------- | --------------------------- |
| Azure Data Factory           | Data ingestion pipelines    |
| Azure Data Lake Storage Gen2 | Cloud data lake storage     |
| Azure Databricks             | Distributed data processing |
| PySpark                      | Data transformation         |
| MongoDB                      | NoSQL data enrichment       |
| Azure Synapse Analytics      | Data warehouse analytics    |
| SQL                          | Analytical queries          |
| Power BI / Tableau / Fabric  | Data visualization          |

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
├── DataIngestionToDB.ipynb
├── Databricks Tranformation.html
├── sql code.txt
├── dataForEachInput.json
├── Architecture Diagram.png
└── README.md
```

---

# Key Data Engineering Practices Implemented

• Medallion architecture (Bronze / Silver / Gold)
• Star schema analytical data modeling
• Parameterized ingestion pipelines
• Metadata-driven pipeline design
• Distributed data processing using PySpark
• Hybrid SQL and NoSQL data integration
• Cloud-based scalable data lake architecture

---

# Author

**Aman Patel**
B.Tech IT — IIIT Vadodara
Aspiring Data Engineer
