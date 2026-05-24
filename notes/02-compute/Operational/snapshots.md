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

---

## Important Commands

## Snapshot Schedules

## Disaster Recovery Notes

## Incremental Snapshot Behavior

## ACE Recognition Patterns

## Common Mistakes
