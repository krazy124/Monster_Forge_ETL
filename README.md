# MonsterForge AWS ETL Pipeline

## Overview

The **MonsterForge AWS ETL Pipeline** is an end-to-end data engineering project demonstrating the design and implementation of a modern cloud-based ETL workflow using AWS and PySpark.

The project ingests raw CSV data, performs automated data quality validation and cleansing with PySpark, separates invalid records into a quarantine dataset, publishes curated datasets to Amazon S3, updates the AWS Glue Data Catalog, and validates the completed pipeline using Amazon Athena.

Rather than focusing on data analysis, this project emphasizes the engineering practices involved in building reliable, repeatable, and production-style data pipelines.

---

## Architecture

```
                Raw CSV
                   │
                   ▼
        Amazon S3 (Raw Landing Zone)
                   │
                   ▼
          PySpark ETL Pipeline
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
   Clean Dataset      Quarantine Dataset
        │                     │
        └──────────┬──────────┘
                   ▼
            Amazon S3 Data Lake
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

## Features

* Automated raw data ingestion
* PySpark data transformation pipeline
* Header normalization
* Whitespace trimming
* Blank value handling
* Data type validation
* Multi-format date parsing
* Currency normalization
* Negative value detection and correction
* Duplicate record detection
* Clean / Quarantine dataset separation
* Amazon S3 versioned storage (`latest` and `run_id`)
* Automated upload verification using boto3
* AWS Glue crawler automation
* Amazon Athena validation queries
* Modular Python design
* Centralized AWS error handling

---

## Technologies

| Technology    | Purpose                          |
| ------------- | -------------------------------- |
| Python        | Pipeline orchestration           |
| PySpark       | Distributed data transformations |
| Amazon S3     | Data lake storage                |
| AWS Glue      | Metadata cataloging              |
| Amazon Athena | SQL validation layer             |
| boto3         | AWS SDK                          |
| Pandas        | Final CSV export                 |
| Git / GitHub  | Version control                  |

---

## Project Structure

```
Monster_Forge_ETL/

├── src/
│   └── monsterforge_etl.py
│
├── data/
│   └── MonsterForge_monsters_raw_100.csv
│
├── docs/
│
├── output/
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## ETL Workflow

1. Upload raw dataset to Amazon S3.
2. Generate a pre-transformation data quality report.
3. Execute PySpark transformations.
4. Detect duplicate records.
5. Split records into clean and quarantine datasets.
6. Export datasets locally.
7. Publish datasets to Amazon S3.
8. Verify uploaded objects.
9. Update the AWS Glue Data Catalog.
10. Validate the published dataset using Amazon Athena.

---

## Sample Pipeline Output

```
========== PIPELINE COMPLETE ==========

Run ID:
20260628_131212

Clean Rows..............84
Quarantine Rows.........21

S3 Upload...............SUCCESS
Athena Validation.......SUCCESS

✓ MonsterForge ETL pipeline completed successfully
```

---

## Skills Demonstrated

* ETL pipeline development
* Cloud data lake architecture
* Data quality validation
* Data cleansing
* AWS service integration
* Data catalog management
* SQL-based validation
* Modular Python development
* Error handling
* Pipeline automation

---

## Future Enhancements

Potential future improvements include:

* Environment-based configuration
* Structured logging
* Quality report generation
* Apache Airflow orchestration
* AWS Lambda event triggers
* Amazon Redshift integration
* Automated unit testing
* Infrastructure as Code

---

## About This Project

This project was developed as part of my transition into Data Engineering with the goal of demonstrating practical experience building cloud-native ETL pipelines using modern AWS services and PySpark.

The emphasis throughout the project is on producing maintainable, modular, and production-oriented code rather than simply demonstrating individual AWS services in isolation.
