# Google Cloud Data Services Decision Tree

This directory contains an architecture decision tree that helps identify the appropriate Google Cloud data service based on application requirements and workload characteristics.

The diagram emphasizes recognition patterns commonly tested on the **Google Cloud Associate Cloud Engineer (ACE)** exam and provides a quick reference for selecting relational, analytical, or NoSQL database services.

---

## Overview

Choosing the correct data platform is a critical architectural decision.

This decision tree guides engineers through common questions such as:

* Is the workload transactional or analytical?
* Is a relational database required?
* Does the application require global scalability?
* Is strong consistency needed across regions?
* Is the workload time-series or IoT focused?

The answers lead to the most appropriate Google Cloud managed data service.

---

## Architecture Diagram

![Google Cloud Data Services Decision Tree](data-solutions-decision-tree.png)

---

## Decision Flow

```text
Data Requirement
        │
        ├── Relational
        │       │
        │       ├── Cloud SQL
        │       │
        │       └── Need Global Scale?
        │               │
        │               └── Cloud Spanner
        │
        ├── Analytics
        │
        │       └── BigQuery
        │
        └── NoSQL / Wide Column
                │
                └── Bigtable
```

---

## Service Recognition Patterns

### Cloud SQL

Best suited for:

* MySQL
* PostgreSQL
* SQL Server
* Traditional relational applications
* Regional deployments
* Vertical scaling

Typical workloads include transactional business applications and web backends.

---

### Cloud Spanner

Best suited for:

* Global relational databases
* Horizontal scaling
* Multi-region deployments
* Strong consistency
* Financial systems
* Large enterprise applications

Recognition pattern:

> If the application requires a relational database **and** global scalability with strong consistency, **Cloud Spanner** is the preferred service.

---

### BigQuery

Best suited for:

* Data warehousing
* OLAP analytics
* Business intelligence
* SQL analytics
* Batch processing
* Streaming ingestion
* Petabyte-scale datasets

Recognition pattern:

> If the workload is analytical rather than transactional, **BigQuery** is usually the correct choice.

---

### Bigtable

Best suited for:

* Time-series data
* IoT telemetry
* Event logging
* High-throughput writes
* Low-latency reads
* Wide-column NoSQL workloads

Recognition pattern:

> If the application stores massive amounts of key-value or time-series data, **Bigtable** is often the preferred solution.

---

## ACE Exam Focus Areas

This diagram supports study objectives related to:

* Cloud SQL
* Cloud Spanner
* BigQuery
* Bigtable
* Relational databases
* NoSQL databases
* Analytics platforms
* Data architecture selection
* Google Cloud managed services

---

## Files Included

| File | Description |
|------------------------------------------|---------------------------------------------|
| `data-solutions-decision-tree.drawio` | Editable draw.io version |
| `data-solutions-decision-tree.png` | Preview image exported from draw.io |
| `data-solutions-decision-tree.svg` | Scalable vector version |
| `storage-selection-architecture.vsdx` | Editable Microsoft Visio version |
| `storage-selection-architecture.png` | Preview image exported from Microsoft Visio |

---

## Created With

- draw.io
- Microsoft Visio Professional
- Google Cloud Architecture Icons
- Custom Google Cloud ACE study annotations

---

## Repository Context

This diagram is part of the **cloud-engineer-learning-path** repository and serves as a visual reference for Google Cloud data service selection, architecture design, and Associate Cloud Engineer certification preparation.


