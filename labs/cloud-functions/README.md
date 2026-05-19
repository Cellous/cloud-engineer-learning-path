

gcloud functions deploy trans_mg_function \
  --runtime python39 \
  --trigger-topic truck_data

  ---

- event-driven architecture
- Pub/Sub triggers
- serverless functions  

---

## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads
gcloud Command Recognition

- gcloud functions deploy → deploying event-driven serverless code.
- gcloud run deploy → deploying containers.
- gcloud sql instances create → creating managed databases
