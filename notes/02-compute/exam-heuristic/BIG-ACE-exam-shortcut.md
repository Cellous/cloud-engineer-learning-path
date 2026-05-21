## ☁️ Cloud Architecture
| Service         | Purpose                |
| --------------- | ---------------------- |
| Compute Engine  | VMs                    |
| GKE             | Kubernetes             |
| Cloud Run       | Serverless containers  |
| Cloud Functions | Event-driven functions |
| Cloud Storage   | Object storage         |
| BigQuery        | Analytics              |
| Cloud SQL       | Managed relational DB  |

---
| If Question Says          | Usually Means                   |
| ------------------------- | ------------------------------- |
| Containers                | Cloud Run or GKE                |
| Event-driven              | Cloud Functions                 |
| Full orchestration        | GKE                             |
| Kubernetes control        | GKE                             |
| Scale to zero             | Cloud Run / App Engine Standard |
| Custom runtime/packages   | Cloud Run                       |
| Minimal ops               | Serverless                      |
| Lightweight functions     | Cloud Functions                 |
| Long-running VM workloads | Compute Engine                  |

---
## Storage Location
| Need                          | Usually Choose |
| ----------------------------- | -------------- |
| Lowest latency in one region  | Regional       |
| Redundancy across two regions | Dual-region    |
| Broad US access               | Multi-region   |
| Worldwide/global users        | Multi-region   |
| Archive rarely used data      | Archive        |
| Read once/month               | Nearline       |
| Read once/quarter             | Coldline       |
| Immediate/frequent access     | Standard       |

---
## Cloud Storage Classes
| Storage Class | Best For         |
| ------------- | ---------------- |
| Standard      | Frequent access  |
| Nearline      | Monthly access   |
| Coldline      | Quarterly access |
| Archive       | Rarely accessed  |

---
## Structured vs Unstructured
| Data Type                  | Usually Means       |
| -------------------------- | ------------------- |
| Structured relational data | Cloud SQL / Spanner |
| Analytics                  | BigQuery            |
| Binary objects/files       | Cloud Storage       |
| Event streams              | Pub/Sub             |
| ETL pipelines              | Dataflow            |

---
## ☁️ Cloud SQL
| Phrase             | Usually Means         |
| ------------------ | --------------------- |
| automatic failover | HA / regional         |
| standby instance   | secondary node        |
| zone outage        | multi-zone redundancy |
| high availability  | regional setup        |
| read scaling       | read replicas         |
| disaster recovery  | replication/failover  |
