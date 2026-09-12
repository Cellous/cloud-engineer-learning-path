# Google Cloud Spanner

## Overview

Spanner is a fully managed relational database service designed for workloads
that require relational database capabilities together with horizontal scale.

Spanner combines:

- SQL support
- Relational schemas
- Strong consistency
- Horizontal scalability
- High availability
- Automatic replication

## When to Consider Spanner

Consider Spanner when:

- A traditional single-instance relational database no longer scales sufficiently
- Database sharding is being used to increase throughput
- Strong transactional consistency is required
- Data must be distributed globally
- High availability is a major requirement
- Multiple relational databases need to be consolidated

Typical use cases include:

- Financial systems
- Inventory systems
- Global transactional applications
- Large-scale mission-critical databases

## Spanner vs Traditional Relational Databases

Traditional relational databases generally provide:

- Schema
- SQL
- Strong consistency
- Primarily vertical scaling

Spanner retains relational capabilities while adding:

- Horizontal scaling
- Automatic replication
- High availability across zones and regions

## Architecture

A Spanner instance can replicate database data across multiple Google Cloud zones.

```text
Spanner Instance
├── Zone 1
│   ├── Database replicas
├── Zone 2
│   ├── Database replicas
└── Zone 3
    └── Database replicas
```

Replication is synchronized across zones using Google's network infrastructure.

This architecture supports:

- High availability
- Regional or multi-region deployments
- Strong consistency
- Geographic distribution

### Architecture Diagrams
- [Spanner Architecture](../../architecture-diagrams/storage/spanner/spanner-architecture.png)
- [Choosing Spanner](../../architecture-diagrams/storage/spanner/choosing-spanner.png)

---

## Cloud SQL vs Spanner
| Requirement                                   | Cloud SQL | Spanner   |
| --------------------------------------------- | --------- | --------- |
| Relational database                           | Yes       | Yes       |
| SQL                                           | Yes       | Yes       |
| Managed service                               | Yes       | Yes       |
| Horizontal scaling                            | Limited   | Yes       |
| Global distribution                           | Limited   | Yes       |
| Strong global consistency                     | Limited   | Yes       |
| Best for ordinary application databases       | Yes       | Sometimes |
| Best for massive/global transactional systems | No        | Yes       |

---

## ACE Recognition Notes

A useful decision shortcut:

**Relational + normal application scale → Cloud SQL**

**Relational + horizontal/global scale + strong consistency → Spanner**

If full relational capability is not required, consider a NoSQL service instead.
