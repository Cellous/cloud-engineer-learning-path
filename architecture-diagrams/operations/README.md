# Operations Flow Across Cymbal Superstore Apps

This diagram documents operational workflows and cloud resource management patterns across multiple Cymbal Superstore applications in Google Cloud.

## Purpose

The goal of this architecture diagram is to demonstrate how different Google Cloud services are managed and operated in production environments as part of Associate Cloud Engineer (ACE) learning and operational recognition practice.

The diagram focuses on:

- Compute operations
- Kubernetes networking
- Data pipeline management
- Bigtable and BigQuery integrations
- Monitoring and observability
- Safe infrastructure updates

---

## Applications Covered

### Supply Chain App
Technologies:
- Compute Engine
- Managed Instance Groups (MIGs)
- Rolling updates

Operational concepts:
- Updating instance templates
- Rolling-action start-update
- Managing VM lifecycle changes
- High availability across zones

---

### Ecommerce App
Technologies:
- Google Kubernetes Engine (GKE)
- Ingress
- External HTTP(S) Load Balancer

Operational concepts:
- External connectivity
- Layer 7 load balancing
- Kubernetes ingress management
- Traffic routing

---

### Transportation App
Technologies:
- Cloud Run
- Dataflow
- Bigtable
- BigQuery External Tables

Operational concepts:
- Streaming analytics
- Bigtable external querying
- JSON table definition files
- BigQuery SQL integrations
- Data pipeline monitoring

---

## Observability Layer

Shared operations tooling includes:

- Monitoring
- Logging
- Alerts
- Dashboards

These services support operational visibility and troubleshooting across all applications.

---

## Recognition Patterns

### Compute Engine Pattern
OS/disk/template changes require:
1. Updating the instance template
2. Performing a rolling-action update
3. Safely propagating changes to VM instances

---

### GKE Networking Pattern
Ingress resources commonly provide:
- Layer 7 HTTP(S) load balancing
- External connectivity
- Global traffic routing

---

### Bigtable + BigQuery Pattern
Bigtable analytics workflows often involve:
1. Creating a JSON table definition file
2. Defining a BigQuery external table
3. Querying data using BigQuery SQL

---

## ACE Exam Focus Areas

This diagram supports learning objectives related to:

- Compute
- Containers
- Data Pipelines
- Observability
- Infrastructure Operations
- Cloud Resource Management

---

## Files Included

- `operations-flow-cymbal-superstore.drawio`
- `operations-flow-cymbal-superstore.png`
- `operations-flow-cymbal-superstore.svg`

---

## Related Technologies

- Google Compute Engine
- Managed Instance Groups
- Google Kubernetes Engine (GKE)
- Cloud Run
- Dataflow
- Bigtable
- BigQuery

---

# Operations Architecture

This section contains operational workflows, cloud administration screenshots, and architecture diagrams related to Google Cloud operational management.

## Snapshot Scheduling

### Snapshot Schedule Creation
![Snapshot Schedule UI](snapshot-schedule-create-ui.png)

### Snapshot Schedule Inventory
![Snapshot Schedule List](snapshot-schedule-list.png)

### Disk Policy Attachment
![Snapshot Disk Policy](snapshot-schedule-disk-policy.png)

## Key Operational Concepts

- Automated backup scheduling
- Snapshot lifecycle management
- Regional vs multi-regional storage
- Disaster recovery preparation
- Compute Engine operational administration

- Google Cloud Observability

---

## Repository

Part of the `cloud-engineer-learning-path` repository focused on Google Cloud architecture, operations, and certification preparation.
