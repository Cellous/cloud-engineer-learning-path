# Google Cloud Storage Lifecycle Policy Flow

This directory contains an architecture diagram illustrating how **Google Cloud Storage (GCS) Lifecycle Management** automatically transitions or deletes objects based on configurable lifecycle conditions.

The diagram highlights the lifecycle evaluation engine, supported conditions, available actions, and resulting storage class transitions that help optimize storage costs and automate data retention.

---

## Overview

Google Cloud Storage Lifecycle Management enables administrators to define policies that automatically manage objects throughout their lifecycle.

Instead of manually moving or deleting files, lifecycle rules evaluate object metadata and execute configured actions when all specified conditions are satisfied.

This feature is commonly used for:

- Cost optimization
- Automated archival
- Data retention policies
- Backup lifecycle management
- Long-term storage optimization

---

## Architecture Diagram

![Google Cloud Storage Lifecycle Policy Flow](gcs-lifecycle-policy-flow.png)

---

## Lifecycle Workflow

```text
Cloud Storage Bucket Objects
                │
                ▼
      Lifecycle Conditions
      ├── CreatedBefore
      ├── MatchesStorageClass
      └── Age
                │
                ▼
     Lifecycle Policy Engine
                │
                ▼
             Actions
      ├── SetStorageClass
      └── Delete
                │
                ▼
     Resulting Storage Classes
      ├── Nearline
      ├── Coldline
      └── Archive
```

---

## Lifecycle Conditions

The lifecycle engine evaluates object metadata against configured conditions.

Supported examples include:

- `age`
- `createdBefore`
- `matchesStorageClass`
- `numNewerVersions`
- `isLive`
- `customTimeBefore`

All configured conditions within a rule must evaluate to **true** before an action is executed.

---

## Lifecycle Actions

### SetStorageClass

Automatically transitions objects into lower-cost storage classes.

Common progression:

```text
STANDARD
      ↓
NEARLINE
      ↓
COLDLINE
      ↓
ARCHIVE
```

This helps reduce storage costs for infrequently accessed data.

---

### Delete

Automatically removes objects that meet retention or expiration requirements.

Typical use cases include:

- Temporary files
- Log retention policies
- Backup expiration
- Compliance cleanup
- Automated storage maintenance

---

## Example Lifecycle Rule

```yaml
condition:
  matchesStorageClass: ["STANDARD"]
  createdBefore: "2026-01-01"

action:
  type: SetStorageClass
  storageClass: NEARLINE
```

This policy moves eligible STANDARD storage objects into the NEARLINE storage class after the specified condition is met.

---

## Storage Class Progression

| Storage Class | Typical Use Case |
|----------------|------------------------------|
| Standard | Frequently accessed data |
| Nearline | Monthly access |
| Coldline | Quarterly access |
| Archive | Long-term archival |

As storage costs decrease, retrieval latency and access costs generally increase.

---

## Recognition Patterns

### Cost Optimization Pattern

If data becomes less frequently accessed over time:

```
STANDARD
      ↓
NEARLINE
      ↓
COLDLINE
      ↓
ARCHIVE
```

Lifecycle Management can automate the transition.

---

### Retention Pattern

If objects exceed a required retention period:

```
Object
      ↓
Lifecycle Evaluation
      ↓
Delete Action
```

No manual intervention is required.

---

## ACE Exam Focus Areas

This diagram supports Associate Cloud Engineer study objectives related to:

- Cloud Storage
- Storage Classes
- Lifecycle Policies
- Cost Optimization
- Object Metadata
- Automated Storage Management
- Backup and Archival Strategies

---

## Files Included

| File | Description |
|-----------------------------------|--------------------------------|
| `gcs-lifecycle-policy-flow.drawio` | Editable draw.io source diagram |
| `gcs-lifecycle-policy-flow.png` | Preview image |
| `gcs-lifecycle-policy-flow.svg` | Scalable vector version |

---

## Created With

- draw.io
- Google Cloud Architecture Icons
- Custom Google Cloud ACE study annotations

---

## Repository Context

This diagram is part of the **cloud-engineer-learning-path** repository and provides a visual reference for Google Cloud Storage Lifecycle Management, storage optimization strategies, and Associate Cloud Engineer certification preparation.


