# Data Solutions Architecture Diagrams

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/Analytics-BigQuery-669DF6?logo=googlebigquery&logoColor=white)
![Cloud Storage](https://img.shields.io/badge/Storage-Cloud_Storage-34A853?logo=googlecloud&logoColor=white)
![Dataflow](https://img.shields.io/badge/Pipeline-Dataflow-FF6F00?logo=googlecloud&logoColor=white)
![ACE](https://img.shields.io/badge/Certification-Associate_Cloud_Engineer-blue)

# Data Solutions Architecture Diagrams

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

## Included Diagrams

### BigQuery Batch Ingestion

Demonstrates scheduled data ingestion using:

- Cloud Storage
- BigQuery Data Transfer Service
- BigQuery

Ideal for:

- Daily reports
- ETL pipelines
- Historical analytics

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

```
data-solutions/
│
├── bigquery-batch-ingestion/
├── batch-vs-streaming/
├── data-service-architecture.png
├── data-service-selection/
    │   ├── README.md
    │   ├── data-solutions-decision-tree.drawio
    │   ├── data-solutions-decision-tree.png
    │   ├── data-solutions-decision-tree.svg
    │   ├── google-cloud-data-service-selection-architecture.png
    │   └── google-cloud-data-service-selection-architecture.vsdx
└── README.md
```

## Portfolio Note

These diagrams were created as part of the **Google Cloud Associate Cloud Engineer Learning Path** to document architectural patterns, improve visual learning, and demonstrate practical understanding of Google Cloud data solutions.
