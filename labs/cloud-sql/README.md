# Cloud SQL Deployment Lab

## Objective

Deploy a Cloud SQL instance for Cymbal Superstore's supply chain application.

---

## Deployment Method

This deployment uses the Google Cloud CLI (`gcloud`).

---

## Example Command

```bash
gcloud sql instances create cymbal_supplychain_db \
--cpu 8 \
--memory 512MB \
--region us-central \
--availability-type=regional
```

---

## Key Parameters

| Parameter | Purpose |
|---|---|
| --cpu | Number of virtual CPUs |
| --memory | Allocated RAM |
| --region | Deployment region |

---

## Concepts Learned

- Managed relational databases
- Regional deployment
- CLI deployment workflows
- Infrastructure automation
- Google Cloud SQL provisioning

---

## Related Services

- Compute Engine
- Cloud SQL
- Internal VPC networking
- HTTPS Load Balancing

---

- HA failover
- regional redundancy
- Cloud SQL vs self-managed MySQL
