# Azure Data Factory End-to-End Data Engineering Pipeline

## Project Overview

This project demonstrates an end-to-end data engineering solution built using Azure Data Factory (ADF) following the Medallion Architecture (Bronze → Silver → Gold) pattern.

The solution ingests data from multiple sources, including on-premises systems, REST APIs, and Azure SQL Database, and processes it through multiple transformation layers to create business-ready datasets for analytics and reporting.

The project is designed using a Parent-Child Pipeline architecture to ensure modularity, scalability, and maintainability.

---

## Architecture

### High-Level Architecture

![Architecture Diagram](images/architecture.png)

```text
On-Premises Source
        │
        ▼
Self Hosted Integration Runtime
        │
        ▼

REST APIs ─────────────┐
                       │
Azure SQL Database ────┤
                       ▼
              Azure Data Factory
                       │
                       ▼
              Bronze Layer (Raw)
                       │
                       ▼
            Silver Layer (Cleaned)
                       │
                       ▼
            Gold Layer (Curated)
```

---

## Technologies Used

- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2
- Azure SQL Database
- Self Hosted Integration Runtime (SHIR)
- REST APIs
- GitHub Integration
- Dynamic Content & Expressions
- Parameterized Pipelines
- Metadata Driven Design
- Medallion Architecture

---

## Solution Architecture

The solution consists of a Parent Pipeline that orchestrates three separate ingestion pipelines and subsequent transformation pipelines.

### Parent Pipeline

The Parent Pipeline acts as the orchestrator and manages the execution flow of all child pipelines.

**Responsibilities:**

- Trigger child pipelines
- Manage dependencies
- Control execution sequence
- Monitor overall workflow

**Screenshot**

![Parent Pipeline](images/parent_pipeline.png)

---

## Child Pipeline 1: On-Premises Data Ingestion

This pipeline is responsible for ingesting data from an on-premises source system.

### Features

- Uses Self Hosted Integration Runtime (SHIR)
- Connects securely to on-premises environment
- Copies source data into Azure Data Lake Storage Gen2
- Loads data into the Bronze layer

### Workflow

1. Connect to On-Premises Source
2. Extract Data
3. Transfer Data via SHIR
4. Store Raw Data in Bronze Layer





<img width="458" height="320" alt="image" src="https://github.com/user-attachments/assets/2feed1fc-5251-477b-9b5e-0543eb060995" />

---

## Child Pipeline 2: API Data Ingestion

This pipeline extracts data from external REST APIs and stores the raw response in the Bronze layer.

### Features

- REST API Integration
- JSON Data Extraction
- Automated Data Loading
- Scalable Design

### Workflow

1. Connect to REST API
2. Retrieve JSON Response
3. Store Raw Data in Data Lake
4. Load into Bronze Layer



<img width="662" height="238" alt="image" src="https://github.com/user-attachments/assets/0c9136d2-e173-4d83-8f91-57b444ac41f2" />


---

## Child Pipeline 3: Azure SQL to Data Lake Ingestion

This pipeline extracts data from Azure SQL Database and loads it into Azure Data Lake Storage Gen2.

### Features

- Azure SQL Integration
- Data Extraction
- Data Lake Loading
- Structured Data Processing

### Workflow

1. Connect to Azure SQL Database
2. Extract Source Tables
3. Load Data into Data Lake
4. Store in Bronze Layer

<img width="1117" height="315" alt="image" src="https://github.com/user-attachments/assets/3b35e6d6-64a9-458c-9a22-6a3763fb076d" />

---

# Medallion Architecture

The project follows the Medallion Architecture pattern to improve data quality and maintainability.

---

## Bronze Layer (Raw Data)

### Purpose

The Bronze Layer stores raw data exactly as received from source systems.

### Characteristics

- No transformations
- Historical data preservation
- Source-level storage
- Auditability

### Data Sources

- On-Premises Systems
- REST APIs
- Azure SQL Database

<img width="1077" height="306" alt="image" src="https://github.com/user-attachments/assets/ed90368a-b57b-453a-ab5a-f2d3b5770ec0" />

---

## Silver Layer (Cleaned Data)

### Purpose

The Silver Layer contains cleansed and standardized data.

### Transformations Performed

- Data Type Conversion
- Null Value Handling
- Data Validation
- Standardization
- Filtering Invalid Records
- Business Rule Application

### Benefits

- Improved Data Quality
- Consistent Data Structure
- Easier Downstream Processing

<img width="1342" height="522" alt="image" src="https://github.com/user-attachments/assets/8d1a3120-c182-494c-a7db-d0173f18d95b" />


---

## Gold Layer (Business Ready Data)

### Purpose

The Gold Layer contains curated datasets optimized for reporting and analytics.

### Transformations Performed

- Aggregations
- Joins
- KPI Calculations
- Business Metrics
- Reporting Views

### Benefits

- Analytics Ready
- Reporting Ready
- Business Friendly Structure

<img width="1326" height="441" alt="image" src="https://github.com/user-attachments/assets/f4fe84df-c04d-4890-a9f4-48282fb049de" />

---

# End-to-End Workflow

1. Parent Pipeline is triggered.
2. On-Premises Ingestion Pipeline executes using Self Hosted Integration Runtime.
3. API Ingestion Pipeline extracts data from external APIs.
4. Azure SQL Ingestion Pipeline loads relational data into Data Lake.
5. Raw data is stored in Bronze Layer.
6. Silver Layer transformations clean and standardize the data.
7. Gold Layer transformations create curated business datasets.
8. Final datasets become available for analytics and reporting.

---

# Key Features

- End-to-End Data Engineering Solution
- Parent-Child Pipeline Architecture
- Self Hosted Integration Runtime Integration
- REST API Data Ingestion
- Azure SQL Database Integration
- Azure Data Lake Storage Gen2
- Medallion Architecture Implementation
- Modular Pipeline Design
- GitHub Source Control Integration
- Reusable and Scalable Framework
- Automated Data Movement
- Enterprise ETL/ELT Design

---

# Learning Outcomes

This project provided hands-on experience with:

- Azure Data Factory
- Data Ingestion Techniques
- Self Hosted Integration Runtime
- REST API Integration
- Azure SQL Database
- Azure Data Lake Storage Gen2
- Medallion Architecture
- Pipeline Orchestration
- GitHub Integration
- ETL/ELT Best Practices
- Enterprise Data Engineering Design Patterns
- ETL/ELT Development
- Data Engineering
- SQL
- GitHub
- Pipeline Orchestration

---
