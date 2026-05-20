

## Example gcloud Commands

### Create Instance Template

```bash
gcloud compute instance-templates create web-template \
    --machine-type=e2-medium \
    --image-family=debian-11 \
    --image-project=debian-cloud
```

### Create Managed Instance Group

```bash
gcloud compute instance-groups managed create web-mig \
    --base-instance-name=web \
    --size=2 \
    --template=web-template \
    --zone=us-central1-a
```

### Enable Autoscaling

```bash
gcloud compute instance-groups managed set-autoscaling web-mig \
    --max-num-replicas=5 \
    --target-cpu-utilization=0.6 \
    --zone=us-central1-a
```
