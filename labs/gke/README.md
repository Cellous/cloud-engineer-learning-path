
## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads

---

gcloud Command Recognition

- gcloud functions deploy → deploying event-driven serverless code.
- gcloud run deploy → deploying containers.
- gcloud sql instances create → creating managed databases

```bash
gcloud container clusters create supply-chain-cluster \
  --zone us-central1-a
```
---

- zonal vs regional clusters
- autopilot vs standard
- Kubernetes orchestration
