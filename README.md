# MonsterForge AWS ETL Pipeline

> **An end-to-end AWS Data Engineering project demonstrating a production-style ETL pipeline built with PySpark, Amazon S3, AWS Glue, Amazon Athena, and boto3.**

---

## Project Highlights

* End-to-end ETL pipeline using PySpark
* Automated data quality validation
* Clean / Quarantine data processing
* Versioned data lake architecture (`latest` + `run_id`)
* AWS Glue Data Catalog automation
* Amazon Athena validation queries
* Modular, reusable Python design
* Centralized AWS error handling

---

## Architecture

> *(Insert architecture diagram here)*

```
Raw CSV
    │
    ▼
Amazon S3 (Raw)
    │
    ▼
PySpark ETL
    │
 ┌──┴──────────┐
 ▼             ▼
Clean      Quarantine
 │             │
 └──────┬──────┘
        ▼
     Amazon S3
           │
           ▼
    AWS Glue Crawlers
           │
           ▼
 AWS Glue Data Catalog
           │
           ▼
    Amazon Athena
           │
           ▼
 Automated Validation
```

---

## Pipeline Features

### Data Quality

* Header normalization
* Whitespace trimming
* Blank value normalization
* Duplicate detection
* Invalid record quarantine
* Multi-format date parsing
* Currency normalization
* Negative value correction
* Data type validation

### AWS Integration

* Amazon S3 uploads
* Object verification
* Versioned storage
* AWS Glue crawler automation
* AWS Glue Data Catalog
* Amazon Athena validation

---

## Example Pipeline Output

```text
========== PIPELINE COMPLETE ==========

Run ID:
20260628_131212

Clean Rows..............84
Quarantine Rows.........21

S3 Upload...............SUCCESS
Glue Crawlers...........SUCCESS
Athena Validation.......SUCCESS

✓ MonsterForge ETL pipeline completed successfully
```

---

## Technologies

| Category        | Technology    |
| --------------- | ------------- |
| Language        | Python        |
| Processing      | PySpark       |
| Cloud           | AWS           |
| Storage         | Amazon S3     |
| Catalog         | AWS Glue      |
| Query Engine    | Amazon Athena |
| SDK             | boto3         |
| Version Control | Git & GitHub  |

---

## Repository Structure

```text
Monster_Forge_ETL/
│
├── src/
│   └── monsterforge_etl.py
│
├── data/
│
├── docs/
│
├── output/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Engineering Decisions

A few design decisions intentionally mirror production ETL pipelines:

* Every pipeline execution generates a unique `run_id` for data lineage.
* Clean and quarantined datasets are written independently.
* The `latest` folder provides easy access to the newest successful dataset.
* Historical pipeline runs remain available for auditing.
* All AWS interactions are centralized through a reusable error-handling wrapper.
* Athena is used as the final validation step after the Glue Data Catalog is updated.

---

## Future Enhancements

Planned improvements include:

* Environment-based configuration
* Structured logging
* Automated quality report generation
* Apache Airflow orchestration
* AWS Lambda event triggers
* Amazon Redshift integration
* Infrastructure as Code (Terraform)

---

## About

This project was built as part of my transition into Data Engineering with the goal of demonstrating practical experience designing, automating, and validating cloud-native ETL pipelines using modern AWS services.

The focus of this repository is on building reliable, maintainable, and production-oriented data engineering workflows rather than performing downstream analytics.
