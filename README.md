# OpenFlow MySQL to Snowflake Demo

End-to-end data engineering project demonstrating **MySQL Change Data Capture (CDC)** ingestion into **Snowflake using Snowflake OpenFlow Gen2**.

The project simulates a multi-database environment where data from several independent MySQL sources is continuously ingested into Snowflake and organized through a layered data architecture.

> **Portfolio project:** This repository is an independent technical demonstration created with fictitious databases, schemas, data, credentials, and infrastructure. It does not contain proprietary information, credentials, or implementation details from any real organization or client.

---

## Architecture

```text
┌─────────────────┐
│    MySQL A      │
│   Demo Source   │
└────────┬────────┘
         │
         │ CDC
         ▼
┌─────────────────┐
│    MySQL B      │
│   Demo Source   │
└────────┬────────┘
         │
         │ CDC
         ▼
┌──────────────────────────────┐
│      Snowflake OpenFlow      │
│            Gen2              │
│                              │
│  Deployment                  │
│      └── Runtime             │
│            └── Connectors    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Snowflake RAW          │
│      Source-aligned data     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Snowflake STAGING       │
│   Cleansing & transformation │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Snowflake ANALYTICS     │
│     Consumption-ready data   │
└──────────────────────────────┘
```

---

## Project Goals

This project demonstrates practical experience with:

* MySQL CDC ingestion
* Snowflake OpenFlow Gen2
* OpenFlow Deployments
* OpenFlow Runtimes
* OpenFlow Connectors
* Secure credential management
* Snowflake database and schema design
* RAW / STAGING / ANALYTICS architecture
* Python-based configuration generation
* Jinja2 templates
* Incremental data ingestion
* Scheduling and runtime management
* Data quality validation
* Troubleshooting ingestion pipelines
* Git and GitHub project management

---

## Technologies

| Technology              | Purpose                                 |
| ----------------------- | --------------------------------------- |
| MySQL                   | Source databases                        |
| Snowflake               | Cloud data platform                     |
| Snowflake OpenFlow Gen2 | Data ingestion and CDC                  |
| Python                  | Automation and configuration generation |
| Jinja2                  | Configuration templating                |
| SQL                     | DDL and data transformation             |
| Git                     | Version control                         |
| GitHub                  | Source code and project documentation   |

---

## Data Flow

The ingestion process follows this general flow:

```text
MySQL
  │
  │ Change Data Capture
  ▼
OpenFlow Connector
  │
  ▼
OpenFlow Runtime
  │
  ▼
Snowflake RAW
  │
  ▼
STAGING
  │
  ▼
ANALYTICS
```

The RAW layer preserves the source-oriented representation of the ingested data.

The STAGING layer applies transformations such as:

* Data type standardization
* String normalization
* Null handling
* Timestamp normalization
* Column naming conventions
* Data quality rules

The ANALYTICS layer contains structures designed for downstream consumption.

---

## OpenFlow Architecture

The project uses the following OpenFlow concepts:

### Deployment

Represents the OpenFlow deployment environment where the data integration infrastructure operates.

### Runtime

Provides the execution environment for OpenFlow dataflows and connectors.

### Connector

Defines the connection and ingestion logic between a source system and the target platform.

Multiple connectors can operate within the same runtime to support multiple MySQL source databases.

---

## Multi-Source Ingestion

The project is designed to demonstrate a scalable pattern for ingesting multiple independent MySQL databases.

For example:

```text
MySQL Demo A ──┐
MySQL Demo B ──┼──> OpenFlow Runtime ──> Snowflake
MySQL Demo C ──┘
```

The source databases use a common logical structure while maintaining independent datasets.

This allows the project to demonstrate how configuration can be generated programmatically instead of manually creating every connector configuration.

---

## Automation

Python and Jinja2 are used to generate OpenFlow configuration files from structured source metadata.

Example conceptual configuration:

```text
sources.yaml
     │
     ▼
Python script
     │
     ▼
Jinja2 template
     │
     ▼
Connector configurations
```

This approach separates:

* Source metadata
* Configuration templates
* Generated configurations
* Deployment logic

Sensitive values are intentionally excluded from version control.

---

## Security

The repository is designed to avoid storing sensitive information in Git.

Examples of excluded information include:

* Passwords
* API keys
* Private keys
* Environment variables
* Credentials
* Secrets
* Generated configurations containing sensitive values

The `.gitignore` file contains rules to prevent accidental commits of sensitive files.

For demonstration purposes, credentials and infrastructure values are fictional.

---

## Project Structure

```text
openflow-mysql-snowflake-demo/
│
├── docs/
│   ├── architecture.md
│   └── runbook.md
│
├── mysql/
│   ├── plant_a.sql
│   ├── plant_b.sql
│   └── plant_c.sql
│
├── openflow/
│   ├── templates/
│   │   └── connector.json.jinja
│   │
│   └── configs/
│
├── scripts/
│   └── generate_configs.py
│
├── snowflake/
│   ├── 01_database.sql
│   ├── 02_schemas.sql
│   └── 03_tables.sql
│
├── .gitignore
└── README.md
```

---

## Documentation

Detailed technical documentation will be maintained under the `docs/` directory.

* **Architecture** — components, data flow, design decisions and relationships.
* **Runbook** — deployment, configuration, execution, validation and troubleshooting procedures.

---

## Learning Objectives

This project is intended to demonstrate practical knowledge of modern data engineering concepts, including:

1. CDC-based data ingestion
2. Cloud data warehousing
3. Data integration architecture
4. Infrastructure and configuration automation
5. Data transformation
6. Security practices
7. Version control
8. Technical documentation
9. Pipeline troubleshooting
10. Scalable multi-source ingestion patterns

---

## Disclaimer

This is an independent portfolio project created for educational and professional demonstration purposes.

All databases, schemas, tables, records, credentials, infrastructure identifiers, network information and configurations are fictitious.
