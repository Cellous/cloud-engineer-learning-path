# Data Solutions Architecture Diagrams

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/Analytics-BigQuery-669DF6?logo=googlebigquery&logoColor=white)
![Cloud Storage](https://img.shields.io/badge/Storage-Cloud_Storage-34A853?logo=googlecloud&logoColor=white)
![Dataflow](https://img.shields.io/badge/Pipeline-Dataflow-FF6F00?logo=googlecloud&logoColor=white)
![ACE](https://img.shields.io/badge/Certification-Associate_Cloud_Engineer-blue)

This directory contains architecture diagrams illustrating common Google Cloud data processing and analytics patterns used in enterprise environments.

The diagrams focus on selecting the appropriate storage, ingestion, and processing technologies based on workload requirements while reinforcing concepts covered in the Google Cloud Associate Cloud Engineer certification.

---

## Architecture Overview

Typical data solution architectures combine storage, messaging, processing, and analytics services to support both batch and real-time workloads.

Examples include:

- Cloud Storage
- BigQuery
- Pub/Sub
- Dataflow
- BigQuery Data Transfer Service

---

## Included Architecture Collections

### BigQuery Analytics

Architecture diagrams covering:

- Partitioning and clustering
- Scheduled query workflows
- External tables
- Looker Studio dashboards
- Enterprise data warehouse patterns
- BigQuery ML

---

### Cloud Storage Patterns

Architecture diagrams covering:

- Object storage design
- Lifecycle policies
- Storage class optimization
- Cost-aware storage management
- Backup and archival strategies

---

### Data Processing Patterns

Architecture diagrams covering:

- Batch processing
- Streaming processing
- Pub/Sub pipelines
- Dataflow architectures
- BigQuery batch ingestion
- Real-time analytics

---

### Data Service Selection

Decision trees and architecture diagrams demonstrating when to choose:

- Cloud SQL
- Cloud Spanner
- Bigtable
- BigQuery
- Cloud Storage

based on workload type, scalability requirements, latency, and consistency needs.

---

### Batch vs Streaming Pipelines

Compares two common ingestion architectures:

| Batch | Streaming |
|----------|-------------|
| Scheduled | Continuous |
| Lower cost | Higher cost |
| Delayed analytics | Real-time analytics |
| Simpler operations | Event-driven architecture |

---

### Data Service Selection

Illustrates when to choose various Google Cloud data services based on workload requirements, latency expectations, and scalability needs.

## Data Services Decision Tree

Directory:

`data-solutions-decision-tree/`

Provides a decision framework for selecting the appropriate Google Cloud data platform based on workload requirements.

Topics include:

- Relational databases
- Analytical workloads
- NoSQL architectures
- Global transaction processing
- Data service selection

Google Cloud services covered:

- Cloud SQL
- Cloud Spanner
- BigQuery
- Bigtable
  
---

## ACE Exam Focus Areas

These diagrams reinforce concepts related to:

- Cloud Storage
- BigQuery
- Pub/Sub
- Dataflow
- Data ingestion
- ETL pipelines
- Streaming analytics
- Batch processing
- Observability
- Cloud architecture design

---

## Recognition Patterns

For the Associate Cloud Engineer exam:

- Cloud Storage → BigQuery generally indicates **batch ingestion**
- Pub/Sub → Dataflow → BigQuery generally indicates **streaming ingestion**
- IoT and event-driven systems typically use **Pub/Sub**
- Historical reporting often relies on **BigQuery batch loading**

---

## Repository Structure

```text
data-solutions/
│
├── bigquery-analytics/
│
├── cloud-storage-patterns/
│
├── data-processing-patterns/
│
└── data-service-selection/
    ├── README.md
    ├── data-solutions-decision-tree.drawio
    ├── data-solutions-decision-tree.png
    ├── data-solutions-decision-tree.svg
    ├── google-cloud-data-service-selection-architecture.png
    └── google-cloud-data-service-selection-architecture.vsdx
```
---

## Learning Objectives

This section demonstrates the ability to:

- Design scalable data architectures
- Select appropriate Google Cloud managed services
- Differentiate batch and streaming pipelines
- Optimize storage and analytics costs
- Apply architectural decision-making patterns
- Build enterprise-ready data platforms

---

## Portfolio Note

This collection was created as part of the **Google Cloud Associate Cloud Engineer Learning Path** and serves as a visual architecture portfolio demonstrating cloud design, data engineering concepts, and enterprise decision-making patterns.

The diagrams emphasize practical service selection, operational workflows, and scalable data platform architectures commonly encountered in modern Google Cloud environments.
