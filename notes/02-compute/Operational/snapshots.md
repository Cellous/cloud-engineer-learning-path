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
### Operational Notes

- Snapshot schedules are attached to Compute Engine disks.
- Resource policies automate recurring backups.
- Policies can be applied during disk creation or afterward.

### Common Operational Workflow

1. Create snapshot schedule
2. Attach policy to disk
3. Monitor retention lifecycle

### Snapshot Schedule UI
 ![Snapshot Schedule Create UI](snapshot-schedule-create-ui.png)

 ![Snapshot Schedule List](snapshot-schedule-list.png)

 ![Snapshot Schedule Disk Policy](snapshot-schedule-disk-policy.png) 
 
---

## Snapshot Chains

Google Cloud snapshots are not isolated backups.

They form:

- dependency chains,
- reference structures,
- downstream relationships.

### Incremental Snapshot Flow


### Snapshot Deletion Behavior

---

## Disaster Recovery Notes

- Snapshots can restore Persistent Disks after failure or corruption.
- Snapshots can create new disks in different zones or regions.
- Snapshots support VM migration and recovery workflows.
- Snapshots are commonly used for:
  - backup recovery
  - rollback operations
  - disaster recovery
  - infrastructure restoration

### Recovery Workflow

1. Create snapshot
2. Store snapshot policy
3. Restore snapshot to new disk
4. Attach restored disk to VM
5. Resume workload operations
### Disaster Recovery Flow

---
## Incremental Snapshot Behavior

- Compute Engine snapshots are incremental by default.
- The first snapshot is a full snapshot.
- Subsequent snapshots only store changed or newly written blocks.
- Unchanged blocks reference previous snapshots.
- Incremental snapshots reduce storage costs and backup time.
- Google Cloud may occasionally create a new full snapshot automatically for storage optimization and reliability.

1. Snapshot 1 stores all disk data.
2. Snapshot 2 stores only changed blocks since Snapshot 1.
3. Snapshot 3 stores only changed blocks since Snapshot 2.
4. Older unchanged blocks are referenced from previous snapshots.

### Snapshot Deletion Behavior

- Deleting a snapshot is irreversible.
- If dependent snapshots exist:
  - required blocks move to downstream snapshots
  - snapshot chain references are updated
  - downstream snapshot size may increase
- Deleting one snapshot does not necessarily delete all stored data.
- To fully remove snapshot data, all dependent snapshots may need removal.
  


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

- `gcloud compute snapshots list`
  → inventory snapshots

- `gcloud compute snapshots describe`
  → detailed snapshot metadata

- Snapshot schedules require:
  - resource policies
  - attachment to Persistent Disks

- You cannot delete a snapshot schedule while attached to a disk.

- Incremental snapshots:
  - reduce storage usage
  - reduce backup cost
  - preserve unchanged block references
    
- Snapshot deletion:
  - may increase downstream snapshot size
  - updates snapshot dependency chains

  
### Recognition Patterns

- Snapshot schedules are configured through resource policies.
- Automated retention reduces manual cleanup.
- "Autodelete snapshots after X days" = lifecycle management.
- Snapshot frequency impacts recovery point objectives (RPO).
  
---
## Common Mistakes

---
## References

- Google Cloud Compute Engine Snapshot Documentation
  https://docs.cloud.google.com/compute/docs/disks/create-snapshots#terraform
