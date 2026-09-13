# Google Cloud Memorystore

## Overview

Memorystore is Google Cloud's fully managed in-memory datastore service.

The course covers:

- Memorystore for Redis
- Memorystore for Redis Cluster
- Memorystore for Valkey

Memorystore is designed for applications that require very low latency,
high throughput, and managed availability without maintaining Redis
infrastructure manually.

---

## Memorystore for Redis

Memorystore for Redis provides a fully managed Redis-compatible
in-memory datastore.

Key characteristics:

- Fully managed service
- In-memory data storage
- Sub-millisecond latency
- High availability
- Automated failover
- Automated patching
- Monitoring
- Redis protocol compatibility
- Lift-and-shift support for Redis applications

According to the course material, Memorystore for Redis supports:

- Instances up to 300 GB
- Network throughput up to 16 Gbps

Because it is Redis protocol compatible, applications using open-source
Redis can be migrated to Memorystore with minimal application changes.

---

## Memorystore for Redis Cluster

Redis Cluster is intended for workloads that outgrow a single Redis
instance.

Important characteristics include:

- Massive scalability
- High throughput
- Ultra-low latency
- Enterprise reliability
- Secure networking
- Multiple shards
- Terabytes of keyspace
- Zero-downtime scaling
- Private Service Connect integration

The course emphasizes Redis Cluster when an application requires
substantially greater scale than a single Memorystore instance.

---

## Memorystore for Valkey

Memorystore for Valkey is based on the open-source Valkey project.

Key concepts covered in the course include:

- Open-source compatibility
- Enhanced performance
- Flexible architectures
- Modern feature support
- High availability
- Cluster Mode Enabled
- Cluster Mode Disabled
- Automated failover

---

## Why Use an In-Memory Datastore?

Traditional databases normally retrieve information from persistent
storage.

An in-memory datastore keeps frequently needed data in memory so that
applications can retrieve it extremely quickly.

Typical uses include:

- Application caching
- Session storage
- Frequently accessed application state
- Real-time data
- Low-latency application responses
- High-traffic applications

A simplified architecture is:

```text
User/Application
       |
       v
  Memorystore
   (cache)
       |
       v
Primary Database
```

---

## Example Cache Flow
```text
Application Request
        |
        v
Is data in Memorystore?
     /       \
   Yes        No
    |          |
Return       Query Database
cached          |
data            v
          Store result
          in Memorystore
                |
                v
          Return result
```

---

## ACE Recognition Notes

Think:

Need extremely fast in-memory access → Memorystore

Useful recognition clues include:

- Redis
- Valkey
- caching
- session data
- sub-millisecond latency
- in-memory datastore
- high-throughput cache
- managed Redis
- automated failover

A useful distinction:
```text
Persistent application database
        ↓
Cloud SQL / Spanner / Firestore / Bigtable

Fast temporary or cached application data
        ↓
Memorystore
```

---

## Connection to Other Google Cloud Services

Memorystore can complement persistent database services rather than
replace them.

Example:
```text
Web Application
      |
      v
Memorystore
(cache/session data)
      |
      v
Cloud SQL
(persistent relational data)
```
This architecture can reduce repeated database queries and improve
application response time.


---
