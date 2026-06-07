# Google Cloud Data Pipelines

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![Data Pipelines](https://img.shields.io/badge/Category-Data_Pipelines-orange)
![Associate Cloud Engineer](https://img.shields.io/badge/Certification-Associate_Cloud_Engineer-blue)

This section contains architecture diagrams and learning resources for common Google Cloud data ingestion and processing patterns.

The diagrams demonstrate how data moves through Google Cloud services using both scheduled and event-driven architectures while emphasizing operational concepts commonly tested on the **Associate Cloud Engineer (ACE)** exam.

---

# Table of Contents

- Overview
- Pipeline Categories
- Architecture Collection
- Common Google Cloud Services
- Operational Concepts
- ACE Exam Focus Areas
- Repository Structure

---

# Overview

Google Cloud supports multiple data ingestion strategies depending on workload requirements.

Some systems process data on a schedule using batch jobs, while others continuously process events in real time using streaming pipelines.

Understanding when to use each architecture is a core cloud engineering skill.

---

# Pipeline Categories

## Batch Processing

Processes data at scheduled intervals.

Characteristics:

- Scheduled execution
- Lower operational complexity
- Cost efficient
- Historical reporting
- ETL workloads

Example technologies:

- Cloud Storage
- BigQuery Data Transfer Service
- BigQuery

---

## Streaming Processing

Processes events continuously as they occur.

Characteristics:

- Near real-time analytics
- Event-driven architecture
- Continuous ingestion
- Low latency
- Highly scalable

Example technologies:

- Pub/Sub
- Dataflow
- BigQuery
- Bigtable

---

# Architecture Collection

## Architecture Collection

| Diagram | Description |
|----------|-------------|
| **Batch vs Streaming Pipeline Flow** | Compares scheduled batch ingestion with event-driven streaming architectures. |
| **BigQuery Batch Ingestion Pipeline** | Demonstrates loading Cloud Storage data into BigQuery using Data Transfer Service. |
| **Pub/Sub → Dataflow Streaming Pipeline** | Demonstrates a real-time event processing architecture using Pub/Sub and Dataflow. |

## Batch vs Streaming Flow

Compares scheduled batch ingestion with event-driven streaming architectures.

Topics include:

- Batch ingestion
- Streaming ingestion
- Operational tradeoffs
- Cost vs latency
- Analytics pipeline design

Folder:

```
batch-vs-streaming-flow/
```

---

## BigQuery Batch Ingestion

Demonstrates scheduled ingestion into BigQuery using Cloud Storage and Data Transfer Service.

Topics include:

- Batch loading
- Scheduled analytics
- Historical reporting
- Cloud Storage integration

Folder:

```
bigquery-batch-ingestion/
```

---

## Pub/Sub → Dataflow Pipeline

Demonstrates a real-time streaming architecture using managed Google Cloud services.

Topics include:

- Event ingestion
- Stream processing
- Analytics pipelines
- Archive storage
- Operational serving

Folder:

```
pubsub-dataflow/
```

---

# Common Google Cloud Services

This section includes architectures involving:

- Cloud Storage
- Pub/Sub
- Dataflow
- BigQuery
- Bigtable
- Cloud Monitoring
- Cloud Logging
- Alerting
- Observability

---

# Operational Concepts

The diagrams reinforce several production architecture patterns:

- Batch processing
- Streaming analytics
- Event-driven design
- Decoupled systems
- Data ingestion
- Analytics pipelines
- Archive storage
- Low-latency serving
- Operational monitoring

---

# ACE Exam Focus Areas

These diagrams support learning objectives related to:

- Pub/Sub
- Dataflow
- BigQuery
- Cloud Storage
- Streaming data
- Batch processing
- Data ingestion
- Analytics
- Cloud operations
- Observability

---

# Repository Structure

```text
data-pipelines/
│
├── README.md
│
├── batch-vs-streaming-flow/
│   ├── README.md
│   ├── batch-vs-streaming-flow.drawio
│   ├── batch-vs-streaming-flow.png
│   └── batch-vs-streaming-flow.svg
│
├── bigquery-batch-ingestion/
│   ├── README.md
│   ├── bigquery-batch-ingestion.drawio
│   ├── bigquery-batch-ingestion.png
│   └── bigquery-batch-ingestion.svg
│
└── pubsub-dataflow/
    ├── README.md
    ├── pubsub-dataflow.drawio
    ├── pubsub-dataflow.png
    └── pubsub-dataflow.svg
```

---

## Learning Path

These diagrams build upon one another:

1. **BigQuery Batch Ingestion**
   - Scheduled data loading
   - Cloud Storage
   - BigQuery Data Transfer Service

↓

2. **Pub/Sub → Dataflow**
   - Event-driven architecture
   - Streaming analytics
   - Real-time processing

↓

3. **Batch vs Streaming Comparison**
   - Architectural tradeoffs
   - Cost vs latency
   - Operational complexity

---

## Associate Cloud Engineer Topics

These diagrams reinforce concepts including:

- Cloud Storage
- Pub/Sub
- Dataflow
- BigQuery
- Data ingestion
- Batch processing
- Streaming analytics
- Event-driven architecture
- Data pipelines
- Cloud Observability
- Operational best practices

---

# Skills Demonstrated

- Google Cloud Architecture
- Data Engineering Fundamentals
- Batch Processing
- Streaming Analytics
- Event-Driven Systems
- Pub/Sub
- Dataflow
- BigQuery
- Cloud Storage
- Bigtable
- Cloud Observability
- Production Pipeline Design
- Streaming Processing
- Analytics Pipelines
- Cloud Operations
- Solution Architecture
- Technical Documentation

---

# Repository

Part of the **cloud-engineer-learning-path** repository documenting Google Cloud architecture patterns, operational workflows, and certification study materials through professionally designed architecture diagrams.
