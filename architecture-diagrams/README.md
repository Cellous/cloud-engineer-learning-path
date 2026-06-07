# Architecture Diagrams

## Compute
- Compute Resource Selection Architecture
- GKE vs Cloud Run
- Serverless vs Server-Based Computing

## Storage
- Storage Selection Architecture
- BigQuery vs Cloud SQL
- Storage Classes Comparison

## Networking
- Google Cloud Load Balancer Types
- Layer 4 vs Layer 7 Traffic Flow
- Regional vs Global Load Balancing

## IAM & Governance
- Resource Hierarchy
- IAM Model
- Billing Architecture
- Observability Scoping

# IAM Architecture Diagrams

Visual reference diagrams for Google Cloud IAM, authentication,
authorization, OAuth flows, service accounts, and workload identity.

## Diagrams Included

- OAuth Service Account Security Flow
- Folder-Level IAM Inheritance
- Workload Identity
- Custom Role Update Flow

## Topics Covered

- OAuth 2.0
- Service Accounts
- IAM Inheritance
- Least Privilege
- Backend Authorization
- Workload Identity
## ACE Recognition Patterns

| Requirement | Usually Means |
|---|---|
| Lowest operational overhead | Autopilot |
| Full customization | Standard GKE |
| Event-driven | Cloud Functions |
| Containers | Cloud Run |
| Rolling updates | Managed Instance Groups |

---

| Folder                               | Source Files              |
| ------------------------------------ | ------------------------- |
| `gke/internal-alb-flow`              | `.drawio`, `.png`, `.svg` |
| `gke/workload-identity`              | `.drawio`, `.png`, `.svg` |
| `iam/iam-resource-model`             | `.vsdx`, `.png`           |
| `iam/resource-hierarchy`             | `.vsdx`, `.png`           |
| `networking/load-balancer-framework` | `.drawio`, `.png`, `.svg` |
| `storage/storage-selection`          | `.vsdx`, `.png`           |
