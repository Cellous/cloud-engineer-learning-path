# Compute Engine Snapshots

## Overview

## Snapshot Concepts
- Snapshots are incremental backups.
- Snapshots can be created while disks are attached to running VMs.
- Snapshots support disaster recovery and VM restoration.
- Snapshots can be used to create new disks or images.
- Snapshot schedules automate backup operations.
---

## Snapshot Commands

### List snapshots
```bash
gcloud compute snapshots list
```
## Snapshot Command Structure
gcloud → group → subgroup → command

Example:
| Part      | Meaning           |
| --------- | ----------------- |
| gcloud    | CLI tool          |
| compute   | service group     |
| snapshots | resource subgroup |
| list      | action command    |

### Describe snapshot
```bash
gcloud compute snapshots describe SNAPSHOT_NAME
```
### Create snapshot
```bash
gcloud compute disks snapshot DISK_NAME \
    --snapshot-names SNAPSHOT_NAME \
    --zone us-central1-a
```
### Create disk from snapshot
```bash
gcloud compute disks create NEW_DISK \
    --source-snapshot SNAPSHOT_NAME \
    --zone us-central1-a
```
### Create Policy
```bash
gcloud beta compute resource-policies create-snapshot-schedule
```
### Attach Policy To Disk
```bash
gcloud beta compute disks add-resource-policies
```
---

## Important Commands
---
## Snapshot Schedules
- Snapshot schedules automate recurring Compute Engine disk backups.
- Schedules can run hourly, daily, or weekly.
- Retention rules automatically delete old snapshots.
- Regional or multi-regional storage locations can be selected.
- Snapshot labels help organize backup policies.
- Common ACE operational task for disaster recovery planning.

### Create Snapshot Schedule via CLI

```bash
gcloud beta compute resource-policies create-snapshot-schedule hourly-schedule \
    --description="create every 6 hours with 15 days retention" \
    --start-time=04:00 \
    --hourly-schedule=6 \
    --max-retention-days=15 \
    --region=europe-west1
```
### Attach Snapshot Policy to Disk

```bash
gcloud beta compute disks add-resource-policies d1 \
    --resource-policies=hourly-schedule \
    --zone=europe-west1-b
```
#### Operational Notes
- Snapshot schedules are attached to Compute Engine disks.
- Resource policies automate recurring backups.
- Policies can be applied during disk creation or afterward.
- Common operational workflow:
- - 1. Create snapshot schedule
- - 2. Attach policy to disk
- - 3. Monitor retention lifecycle

### Snapshot Schedule UI
 
---
## Disaster Recovery Notes
### Disaster Recovery Flow

---
## Incremental Snapshot Behavior
### Incremental Snapshot Diagram

---
## ACE Recognition Patterns
- snapshots belong under Compute Engine
- snapshots commands use:
  ```bash
  gcloud compute snapshots
- "list" and "describe" are common ACE command verbs
- snapshots support disaster recovery
- snapshots can create new disks and images
- snapshot schedules automate backups
- snapshots are incremental after first backup
  
### Recognition Patterns

- Snapshot schedules are configured through resource policies.
- Automated retention reduces manual cleanup.
- "Autodelete snapshots after X days" = lifecycle management.
- Snapshot frequency impacts recovery point objectives (RPO).
---
## Common Mistakes
