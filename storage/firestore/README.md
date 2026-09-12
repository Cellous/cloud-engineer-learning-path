# Google Cloud Firestore

## Overview

Firestore is a fully managed, serverless, cloud-native NoSQL document database.

It is designed for applications that need scalable storage, synchronization,
and querying without managing database infrastructure.

## Key Capabilities

- NoSQL document database
- Fully managed and serverless
- Automatic scaling
- Live synchronization
- Offline support
- ACID transactions
- Multi-region replication
- Strong consistency
- Powerful query support
- Firebase and Google Cloud integration

## Common Use Cases

Firestore is well suited for:

- Mobile applications
- Web applications
- IoT applications
- User profiles
- Game state
- Applications with changing or flexible schemas
- Applications requiring real-time updates

## Data Model

Firestore Native mode uses:

- Collections
- Documents
- Fields

A simplified structure might look like:

```text
users
├── user-001
│   ├── name
│   ├── email
│   └── preferences
└── user-002
```
A useful distinction from the course:
    ├── name
    ├── email
    └── preferences
---

## Firestore Modes
### Native Mode

Designed for modern mobile and web applications.

Provides:

- Collection/document data model
- Real-time updates
- Mobile and web client libraries
- Strong consistency

### Datastore Mode

Provides compatibility with Datastore APIs and application behavior.

This can be useful for applications that need Datastore compatibility while
using Firestore's underlying storage infrastructure.

## When to Consider Firestore

Consider Firestore when:

- The schema may change over time
- The application needs an adaptable document database
- The workload should scale down to zero
- Low operational overhead is important
- The database needs to scale to large workloads
- Mobile or web applications need real-time synchronization

## Firestore vs Bigtable

| Requirement                       | Firestore  | Bigtable           |
| --------------------------------- | ---------- | ------------------ |
| Document database                 | Yes        | No                 |
| Flexible application data model   | Yes        | Limited            |
| Serverless application use        | Strong fit | Different use case |
| Scale to zero                     | Yes        | No                 |
| Transactional consistency         | Supported  | Different model    |
| Massive high-throughput workloads | Sometimes  | Strong fit         |
| Mobile/web integration            | Strong     | No                 |

---

## ACE Recognition Notes

Flexible schema + application data + serverless → Firestore
```text
Mobile/web + real-time synchronization → Firestore
```
Massive throughput / very large NoSQL analytical or lookup workloads → consider Bigtable

## Key Takeaway

Firestore is a managed NoSQL document database designed for scalable,
low-maintenance application workloads, especially mobile and web applications.
