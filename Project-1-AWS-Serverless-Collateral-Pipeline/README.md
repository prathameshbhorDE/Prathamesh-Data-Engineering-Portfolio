# AWS Serverless Collateral Data Pipeline

## Overview

This project demonstrates an end-to-end serverless data engineering pipeline built on AWS for processing collateral management data used in investment banking and fund administration workflows.

The solution automates data validation, ETL processing, metadata cataloging, analytics, orchestration, monitoring, and business reporting using fully managed AWS services.

The project was inspired by real-world collateral management operations and simulates how financial institutions process exposure, margin, collateral, and counterparty data.

---

## Architecture Diagram

![Architecture Diagram](screenshots/architecture-diagram.png)

---

## Business Problem

Financial institutions process large volumes of collateral management data daily.

Manual validation and reporting create:

* Delayed reporting
* Data quality issues
* Operational risk
* Limited visibility into exposure and margin requirements

This pipeline automates the entire process using AWS serverless services.

### Data Processed

The dataset contains:

* Counterparty Name
* Region
* Total Collateral
* Initial Margin
* Total Exposure
* Margin Call Payments
* Margin Recall Amounts

### Business Outcome

The solution provides:

* Automated validation
* Data quality controls
* ETL processing
* Analytics-ready datasets
* Automated notifications
* Tableau dashboards for business users

---

## Technology Stack

### AWS Services

* Amazon S3
* AWS Lambda
* AWS Glue
* AWS Glue Crawler
* AWS Athena
* AWS Step Functions
* Amazon SNS
* Amazon CloudWatch
* AWS IAM

### Languages

* Python
* SQL
* PySpark

### Visualization

* Tableau Public

---

## Data Architecture

Bronze / Silver / Gold Lakehouse Design

```text
Raw Data
    ↓
Bronze Layer
    ↓
Silver Layer
    ↓
Gold Layer
    ↓
Athena Analytics
    ↓
Tableau Dashboard
```

---

## End-to-End Workflow

### Step 1 — Data Ingestion

Collateral CSV files are uploaded into the Bronze S3 bucket.

---

### Step 2 — Data Validation

AWS Lambda validates:

* Required columns
* Region values
* Numeric fields
* File structure

Valid files move forward.

Invalid records are routed to Invalid and Error folders.

---

### Step 3 — Workflow Orchestration

AWS Step Functions orchestrates:

1. Validation
2. ETL Processing
3. Metadata Refresh
4. Notifications

---

### Step 4 — ETL Processing

AWS Glue performs:

* Data cleansing
* Column normalization
* Exposure calculations
* Margin calculations
* Business aggregations

---

### Step 5 — Gold Layer Creation

Aggregated datasets are stored in Parquet format within the Gold layer.

Benefits:

* Faster queries
* Reduced storage
* Analytics optimization

---

### Step 6 — Metadata Management

AWS Glue Crawler updates the Data Catalog.

Athena tables are automatically refreshed.

---

### Step 7 — Analytics Layer

Athena queries are executed directly on Gold datasets.

Examples:

* Exposure by Region
* Counterparty Rankings
* Margin Call Analysis
* Net Exposure Metrics

---

### Step 8 — Notifications

Amazon SNS sends:

* Success Alerts
* Failure Alerts

to subscribed email addresses.

---

### Step 9 — Business Reporting

Tableau dashboards provide:

* Regional Exposure Analysis
* Margin Call Monitoring
* Counterparty Risk Analysis
* Exposure Distribution

---

## Screenshots

### S3 Data Lake Structure

![S3](screenshots/s3-structure.png)

---

### Gold Layer Parquet Output

![Gold](screenshots/gold-layer.png)

---

### Lambda Validation Function

![Lambda](screenshots/lambda-validation.png)

---

### AWS Glue ETL Job

![Glue](screenshots/glue-job.png)

---

### Athena Analytics

![Athena](screenshots/athena-query.png)

---

### Step Functions Workflow

![StepFunctions](screenshots/step-functions.png)

---

### SNS Email Notification

![SNS](screenshots/sns-notification.png)

---

### Tableau Dashboard

![Dashboard](screenshots/tableau-dashboard.png)

---

## Key Features

* Serverless Architecture
* Event-Driven Processing
* Automated Validation
* Bronze/Silver/Gold Design
* Metadata Cataloging
* Parquet Optimization
* Automated Notifications
* Tableau Reporting

---

## Challenges Faced

### Data Validation Logic

Challenge:

Handling missing columns and invalid data formats.

Resolution:

Implemented Lambda validation rules before ETL execution.

---

### IAM Permissions

Challenge:

Multiple services required cross-service permissions.

Resolution:

Created dedicated IAM roles with least-privilege access.

---

### Glue Metadata Synchronization

Challenge:

Athena tables were not reflecting new datasets.

Resolution:

Integrated Glue Crawlers into workflow orchestration.

---

### ETL Transformation Logic

Challenge:

Financial datasets contained inconsistent column names.

Resolution:

Implemented column normalization using PySpark.

---

## Results

Successfully processed:

* 500+ collateral records
* Automated end-to-end workflow
* Gold Layer Parquet generation
* Athena analytics integration
* Tableau dashboard reporting

Performance improvements achieved through:

* Serverless architecture
* Parquet optimization
* Automated orchestration

---

## Key Learnings

* AWS Serverless Architecture
* Data Lake Design
* ETL Engineering
* Data Quality Management
* Metadata Cataloging
* Cloud Monitoring
* Workflow Orchestration
* Financial Data Processing

---

## Future Enhancements

* Infrastructure as Code using Terraform
* CI/CD Pipeline using GitHub Actions
* Apache Airflow Orchestration
* Spark-Based Processing
* Data Quality Framework
* Real-Time Streaming Integration
* Databricks Implementation

---

## Repository Structure

```text
Project-1-AWS-Serverless-Collateral-Pipeline/

├── screenshots/
├── architecture/
├── lambda/
├── glue-jobs/
├── sql/
├── documentation/
└── README.md
```

---

## Author

Prathamesh Bhor

Investment Banking Operations → Data Engineering Transition

Technologies:

AWS | Python | SQL | Glue | Athena | Lambda | Step Functions | Tableau

---
