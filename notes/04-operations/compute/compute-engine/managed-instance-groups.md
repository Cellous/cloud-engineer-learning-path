# Compute Engine / Managed Instance Groups
Need VM scaling + zonal resilience
→ Managed Instance Groups (MIG)

Need rolling updates
→ rolling-action start-update

Need OS/disk/template changes
→ Update instance template
→ Propagate changes to MIG

## Important command pattern:
```
gcloud compute instance-groups managed rolling-action start-update
```
