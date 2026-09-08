# Create and Manage Cloud Storage Buckets and Encryption

## Skills Practiced

- Create Cloud Storage buckets
- Configure object ACLs
- Use customer-supplied encryption keys (CSEK)
- Configure `.boto`
- Rotate CSEK keys
- Configure lifecycle management
- Enable object versioning
- Synchronize directories
- Configure cross-project IAM access

## Key Commands

```bash
export BUCKET_NAME_1=<bucket-name>
gcloud storage cp setup.html gs://$BUCKET_NAME_1/
gsutil config -n
nano .boto
```

## Lab Objectives

This lab applies several Google Cloud Storage concepts through hands-on configuration.

### Tasks Covered

- Create Cloud Storage buckets
- Configure Access Control Lists (ACLs)
- Limit access to stored data
- Configure customer-supplied encryption keys
- Enable object versioning
- Configure Object Lifecycle Management
- Automatically archive or delete objects based on lifecycle rules
- Use directory synchronization

---

## Concepts Reinforced

This lab reinforces concepts documented in:

- Cloud Storage bucket and object architecture
- Access control
- ACLs
- Encryption
- Object versioning
- Object Lifecycle Management
- Directory synchronization
