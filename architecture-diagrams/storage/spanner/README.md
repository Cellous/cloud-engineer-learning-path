# Google Cloud Spanner Architecture Diagrams

This directory contains editable and rendered diagrams used to document
Google Cloud Spanner architecture and service-selection concepts.

## Diagrams

### Spanner Architecture

Illustrates:

- A Spanner instance spanning multiple zones
- Database replicas across zones
- Synchronous data replication
- Cross-zone update propagation

Files:

- `spanner-architecture.drawio`
- `spanner-architecture.png`
- `spanner-architecture.svg`

### Choosing Spanner

Decision diagram showing when Spanner should be considered instead of
Cloud SQL or a NoSQL database.

Key decision factors include:

- Outgrowing a single-instance relational database
- Database sharding for throughput
- Transactional consistency
- Global data with strong consistency
- Database consolidation
- Need for full relational capability

Files:

- `choosing-spanner.drawio`
- `choosing-spanner.png`
- `choosing-spanner.svg`
