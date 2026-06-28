# MonsterForge AWS ETL Pipeline

> **An end-to-end AWS Data Engineering project demonstrating a production-style ETL pipeline built with PySpark, Amazon S3, AWS Glue, Amazon Athena, and boto3.**

---

## Project Highlights

- End-to-end ETL pipeline using PySpark
- Automated data quality validation
- Clean / Quarantine data processing
- Versioned data lake architecture (`latest` + `run_id`)
- AWS Glue Data Catalog automation
- Amazon Athena validation queries
- Modular, reusable Python design
- Centralized AWS error handling

---

## Architecture

![MonsterForge AWS ETL Architecture](docs/images/diagrams/architecture.png)

---

## Amazon S3 Data Lake

The ETL pipeline organizes data into separate storage zones for raw ingestion, clean datasets, quarantined records, reporting, and Athena query results.

### S3 Bucket Layout

![Amazon S3 Root Bucket](docs/images/s3_screenshots/s3-root.png)

### Raw Zone

![Amazon S3 Raw Zone](docs/images/s3_screenshots/s3_raw_zone.png)

### Clean Zone

![Amazon S3 Clean Zone](docs/images/s3_screenshots/s3_clean_zone.png)

### Quarantine Zone

![Amazon S3 Quarantine Zone](docs/images/s3_screenshots/s3_qurantine_zone.png)

### Reports Zone

![Amazon S3 Reports Zone](docs/images/s3_screenshots/s3_report_zone.png)

---

## Pipeline Features & AWS Integration

- Amazon S3 uploads
- Object verification
- Versioned storage
- AWS Glue crawler automation
- AWS Glue Data Catalog
- Amazon Athena validation

### Terminal Output

#### Pre-Transformation Quality Report

![Pre-Transformation Quality Report](docs/images/terminal_screenshots/terminal_1.png)

#### Raw Dataset Preview

![Raw Dataset Preview](docs/images/terminal_screenshots/terminal_2.png)

---

## Data Quality Transformations

- Header normalization
- Whitespace trimming
- Blank value normalization
- Duplicate detection
- Invalid record quarantine
- Multi-format date parsing
- Currency normalization
- Negative value correction
- Data type validation

#### Transformation Pipeline

![Transformation Pipeline](docs/images/terminal_screenshots/terminal_3.png)

---

## Example Pipeline Output

#### Clean Dataset

![Clean Dataset Preview](docs/images/terminal_screenshots/terminal_4.png)

#### Clean / Quarantine Summary

![Pipeline Summary](docs/images/terminal_screenshots/terminal_5.png)

#### S3 Upload Verification

![Amazon S3 Upload Verification](docs/images/terminal_screenshots/terminal_6.png)

#### Athena Validation & Pipeline Completion

![Athena Validation](docs/images/terminal_screenshots/terminal_7.png)

---

## Technologies

| Category | Technology |
|----------|------------|
| Language | Python |
| Processing | PySpark |
| Cloud | Amazon Web Services (AWS) |
| Storage | Amazon S3 |
| Metadata Catalog | AWS Glue |
| Query Engine | Amazon Athena |
| SDK | boto3 |
| Version Control | Git & GitHub |

---

## Engineering Decisions

A few design decisions intentionally mirror production ETL pipelines:

- Every pipeline execution generates a unique `run_id` for data lineage.
- Clean and quarantined datasets are written independently.
- The `latest` folder provides a stable endpoint for downstream consumers.
- Historical pipeline runs are preserved for auditing and traceability.
- All AWS interactions are centralized through a reusable error-handling wrapper.
- Amazon Athena performs post-load validation after the AWS Glue Data Catalog has been updated.

---

## Future Enhancements

Planned improvements include:

- Environment-based configuration
- Structured logging
- Automated quality report generation
- Apache Airflow orchestration
- AWS Lambda event triggers
- Amazon Redshift integration
- Infrastructure as Code (Terraform)

---

## About

This project was built as part of my transition into Data Engineering with the goal of demonstrating practical experience designing, automating, and validating cloud-native ETL pipelines using modern AWS services.

The focus of this repository is on building reliable, maintainable, and production-oriented data engineering workflows rather than performing downstream analytics.